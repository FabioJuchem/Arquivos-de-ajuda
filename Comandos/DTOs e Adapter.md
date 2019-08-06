### Dependências

Properties

```
<mandala-common-app.version>1.1.1.0</mandala-common-app.version>
```

Dependencia

```
<dependency> 
<groupId>br.com.db1.mandala</groupId>  
<artifactId>mandala-common-app</artifactId>  
<version>${mandala-common-app.version}</version>
</dependency>
```









package br.com.db1.mandala.mandalacommonapp;

public class PessoaService {
private PessoaAdapter pessoaAdapter;
    

    @Transactional
public PessoaResponseDTO save(PessoaPersistDTO pessoaPersistDTO) {
var pessoa = pessoaAdapter.toEntity(pessoaPersistDTO);
        return pessoaAdapter.toResponse(pessoaRepository.save(pessoa));
    }
}



package br.com.db1.mandala.mandalacommonapp;

import br.com.db1.mandala.mandalacommonapp.adapter.EntityAdapter;
import org.modelmapper.ModelMapper;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Component;

@Component
	public class PessoaAdapter implements EntityAdapter<Pessoa, PessoaPersistDTO, 			              PessoaResponseDTO> {

@Autowired
     	private ModelMapper mapper;





    @Override
    
    public Pessoa toEntity(PessoaPersistDTO dto) {
​				return mapper.map(dto, Pessoa.class);

 }

@Override
  	public PessoaResponseDTO toResponse(Pessoa pessoa) {
return mapper.map(pessoa, PessoaResponseDTO.class);
    }



@Override
   	 public void updateEntity(Pessoa pessoa, PessoaPersistDTO dto) {
mapper.map(dto, pessoa);
    }
}