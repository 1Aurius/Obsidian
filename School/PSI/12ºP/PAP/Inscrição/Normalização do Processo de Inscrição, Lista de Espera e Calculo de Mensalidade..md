

Neste documento encontra-se a normalização dos 3 Processos já referidos tanto como a justificação e explicação de quais queres duvidas que me tenham ocorrido ao longo da mesma.
### Não Normalizado
isto é um conjunto de campos recolhidos da ficha de inscrição, estes levam em consideração varios aspetos tanto da criança como do seu respetivo aglomerado familiar. Estes são levados em conta no calculo da mensalidade e posição na lista de espera.

Inscricao = id                                 
			      + crianca_id
			      + ordem                                
			      + al              
			      + dt_validada     
			      + dt_inicio_freq  
			      + estado          
			      + last_coms  
			      + foto           
			      + sala           
			      + tipo_morada_c   
			      + contrato        
			      + morada_id  
			      + rl_pai_id   
			      + rl_mae_id   
			      + rl_outro_id 
			      + tipo_ee         
			      + motivo_outro_rl 
			      + atendimento_id
			      + familiar_user_id
			      + familiar_parentesco_id
			      + is_necessario_apoio_especial
			      + apoio_especial
			      + qtd_irmaos_no_jdi,
				  + aus_indisp_pais,
				  + reside_area_instituiao,
				  + is_familiar_de_colaborador,
				  + get_recursos_agregado_familiar,
				  + is_encaminhado_de_outros_serv,
				  + get_outros_serv,
				  + is_integrado
				  + agregado_familiar_de_RSI
				  + pensao_alimentos
				  + agregado_familiar_benef_desemprego
				  + tipo_habitacao
				  + medicacao_cronica
				  + renda_casa_emprestimo_brancario
				  + despesas_outro
				  + motivo_frequencia
				  + visita_instalacoes_do_jdi
				  + created_at,
				  + updated_at,
				  + deleted_at



### F1
Nesta fase indentificam-se as chaves primarias e chaves externas, ou seja as chaves que irão turnar cada "row" unica e os campos cujos valores vão estar associados aos de outras tabelas.

##### Perguntas a fazer
A combinação de todas as colunas cria uma linha única todas as vezes?
Qual campo pode ser usado para identificar exclusivamente a linha?


Inscricao = id(PK)                                 
			      + crianca_id(FK) 
			      + ordem                                
			      + al              
			      + dt_validada     
			      + dt_inicio_freq  
			      + estado          
			      + last_coms  
			      + foto           
			      + sala           
			      + tipo_morada_c   
			      + contrato        
			      + morada_id  (FK)
			      + rl_pai_id  (FK) 
			      + rl_mae_id  (FK) 
			      + rl_outro_id(FK) 
			      + tipo_ee         
			      + motivo_outro_rl 
			      + atendimento_id(FK)  
			      + familiar_user_id(FK)
			      + familiar_parentesco_id(FK)
			      + is_necessario_apoio_especial
			      + apoio_especial
			      + qtd_irmaos_no_jdi,
				  + aus_indisp_pais,
				  + reside_area_instituiao,
				  + is_familiar_de_colaborador,
				  + get_recursos_agregado_familiar,
				  + is_encaminhado_de_outros_serv,
				  + get_outros_serv,
				  + is_integrado
				  + agregado_familiar_de_RSI
				  + pensao_alimentos
				  + agregado_familiar_benef_desemprego
				  + tipo_habitacao
				  + medicacao_cronica
				  + renda_casa_emprestimo_brancario
				  + despesas_outro
				  + motivo_frequencia
				  + visita_instalacoes_do_jdi
				  + created_at,
				  + updated_at,
				  + deleted_at
### F2

Nesta fase garantimos que todos os campos presentes na tabela dependem solamente da PK sendo que se não, fazemos varias tabelas para que diferentes campos fiquem nos seus logares corretos.

##### Perguntas a fazer
Cumprir os requisitos da primeira forma normal
Cada atributo não-chave deve ser funcionalmente dependente da chave primária

Inscricao = id(PK)                                 
			      + crianca_id(FK) 
			      + ordem                                
			      + al              
			      + dt_validada     
			      + dt_inicio_freq  
			      + estado          
			      + last_coms  
			      + foto           
			      + sala           
			      + tipo_morada_c   
			      + contrato        
			      + morada_id  (FK)
			      + rl_pai_id  (FK) 
			      + rl_mae_id  (FK) 
			      + rl_outro_id(FK) 
			      + tipo_ee         
			      + motivo_outro_rl 
			      + atendimento_id(FK)  
			      + familiar_user_id(FK)
			      + familiar_parentesco_id(FK)
			      + is_necessario_apoio_especial
			      + apoio_especial
                  + motivo_frequencia
				  + created_at,
				  + updated_at,
				  + deleted_at
<><><><><><><><><><><><><><><><><><><><>
Lista de Espera = id(PK)
				  + inscricao_id(FK)
				  + is_integrado 
				  + qtd_irmaos_no_jdi,
				  + aus_indisp_pais,
				  + reside_area_instituiao,
				  + is_familiar_de_colaborador,
				  + get_recursos_agregado_familiar,
				  + is_encaminhado_de_outros_serv,
				  + get_outros_serv,
				  + created_at,
				  + updated_at,
				  + deleted_at
<><><><><><><><><><><><><><><><><><><><><>
Mensalidade = id(PK)
				  + Inscricao_id(PK,FK)
				  + agregado_familiar_de_RSI
                  + pensao_alimentos
                  + agregado_familiar_benef_desemprego
                  + tipo_habitacao
                  + medicacao_cronica
                  + renda_casa_emprestimo_brancario
                  + despesas_outro


Acabamos com a divisão da inscrição original em 3 tabelas, com as relações

| tabela 1  | Relação | tabela 2        |
| --------- | ------- | --------------- |
| Inscrição | 1:1     | Mensalidade     |
| Inscrição | 1:1     | Lista de Espera |

Refiro a minha aproximação á lista de espera, sendo que se uma criança fizer uma inscrição e ficar registada a sua posição na lista de espera ,creio , podermos reutilizar essa posição, isto pode estar sobre revisão.