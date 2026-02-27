**Projeto API**

API REST simples para cadastro e gestão de `Medico` e `Paciente`, construída com Spring Boot, JPA, migrações SQL (Flyway) e o Lombok em classes DTO.

**Requisitos**
- **Java**: JDK 17+ instalado.
- **Maven**: wrapper incluído (`mvnw` / `mvnw.cmd`).
- **Banco**: MySQL (ou outro compatível) configurado em `src/main/resources/application.properties`.

**Executando localmente**
- Usando o wrapper (Windows):

```powershell
mvnw.cmd spring-boot:run
```

- Gerar JAR e executar:

```powershell
mvnw.cmd clean package -DskipTests
java -jar target\*.jar
```

**Endpoints principais**
- **Medicos**:
  - `POST /medicos` — cadastrar médico (body: `DadosCadastroMedico`).
  - `GET /medicos` — listar médicos ativos (paginação via `Pageable`).
  - `PUT /medicos` — atualizar médico (body: `DadosAtualizacaoMedico`).
  - `DELETE /medicos/{id}` — desativar médico (marca `ativo = false`).
- **Pacientes**:
  - `POST /pacientes` — cadastrar paciente (body: `DadosPaciente`).
  - `GET /pacientes` — listar pacientes ativos (paginação).
  - `PUT /pacientes` — atualizar paciente.
  - `DELETE /pacientes/{id}` — desativar paciente.

**Banco de dados & migrações**
- As migrações SQL estão em [src/main/resources/db/migration](src/main/resources/db/migration).

**Observações**
- Validações de entrada são feitas com `@Valid` e classes `Dados*`.
- Paginação usa `Pageable` (veja uso em controllers).

**Próximos passos sugeridos**
- Ajustar `application.properties` com credenciais locais do banco.
- Rodar migrações e testar endpoints com `curl` ou Postman.
