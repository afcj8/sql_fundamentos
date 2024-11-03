# 13. Gatilhos

Um gatilho (trigger) é uma função automatizada que é acionada em resposta a eventos específicos em uma tabela ou visão. Triggers são amplamente utilizados para manter a integridade dos dados, automatizar processos e realizar auditorias, entre outras finalidades.

Um trigger é composto por duas partes principais:

1. **Evento de Disparo:** é o evento que ativa o trigger, podendo ser operações de modificação como `INSERT`, `UPDATE`, ou `DELETE`.
2. **Função de Trigger:** é a função que define as ações a serem executadas quando o trigger é ativado. No PostgreSQL, essas funções são criadas separadamente e associadas ao trigger.

Os triggers podem ser configurados para serem executados antes ou depois do evento. Quando executado antes, ele pode modificar os dados antes de serem salvos no banco; quando depois, ele permite registrar ou auditar mudanças após a execução do evento.

Triggers são úteis para:

- **Manter Integridade de Dados:** ajudam a garantir que os dados inseridos ou modificados atendam a determinadas condições.
- **Auditoria e Log:** registram automaticamente mudanças ou tentativas de acesso a uma tabela.
- **Automação de Processos:** simplificam operações complexas que precisam ocorrer em conjunto com modificações na tabela.

**Exemplos de Uso de Triggers**

1. **Atualizar Data de Modificação:** Um trigger pode atualizar automaticamente uma coluna `updated_at` sempre que uma linha é alterada.

```
CREATE OR REPLACE FUNCTION atualiza_data_modificacao()
RETURNS TRIGGER AS $$
BEGIN
   NEW.updated_at = NOW();
   RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER atualiza_data_modificacao_trigger
BEFORE UPDATE ON minha_tabela
FOR EACH ROW
EXECUTE FUNCTION atualiza_data_modificacao();
```