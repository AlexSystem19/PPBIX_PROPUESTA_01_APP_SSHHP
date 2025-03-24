# Data Model Documentation

## Table: TAB_CATEGORIA

### Columns:

- **ID_CAT**: Type: int64   , Summarized by: none
- **CATEGORIA**: Type: string   , Summarized by: none


### Partitions:

- **Name**: TAB_CATEGORIA, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    TAB_CATEGORIA_Table = Origen{[Item="TAB_CATEGORIA",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(TAB_CATEGORIA_Table,{{"ID_CAT", Int64.Type}, {"CATEGORIA", type text}})
in
    #"Tipo cambiado"
```


## Table: TAB_OBSERVACION

### Columns:

- **ID_OBS**: Type: int64   , Summarized by: none
- **CATEGORIA OBSERVACION**: Type: string   , Summarized by: none

### Partitions:

- **Name**: TAB_OBSERVACION, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    TAB_OBSERVACION_Table = Origen{[Item="TAB_OBSERVACION",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(TAB_OBSERVACION_Table,{{"ID_OBS", Int64.Type}, {"CATEGORIA OBSERVACION", type text}})
in
    #"Tipo cambiado"
```


## Table: TAB_RESUMEN

### Columns:

- **ID_CLI**: Type: int64   , Summarized by: none
- **ID_CAT**: Type: int64   , Summarized by: none
- **FECHA**: Type: dateTime   , Summarized by: none
- **ID_OBS**: Type: int64   , Summarized by: none
- **ID_SUP**: Type: int64   , Summarized by: none

### Partitions:

- **Name**: TAB_RESUMEN, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    TAB_RESUMEN_Table = Origen{[Item="TAB_RESUMEN",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(TAB_RESUMEN_Table,{{"ID_CLI", Int64.Type}, {"ID_CAT", Int64.Type}, {"FECHA", type date}, {"ID_OBS", Int64.Type}, {"ID_SUP", Int64.Type}})
in
    #"Tipo cambiado"
```


## Table: DateTableTemplate_97cc582e-db97-429f-b2e0-c9e396630da3

### Columns:

- **Date**: Type: dateTime  (Hidden)  , Summarized by: none
- **Año**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **NroMes**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Mes**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **NroTrimestre**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Trimestre**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **Día**: Type: int64  (Hidden)  (Calculated) , Summarized by: none

### Partitions:

- **Name**: DateTableTemplate_97cc582e-db97-429f-b2e0-c9e396630da3, **Mode**: import, **Expression**: 
```
Calendar(Date(2015,1,1), Date(2015,1,1))
```


## Table: LocalDateTable_f05f7ddd-2f16-41de-a870-85a6c9becf36

### Columns:

- **Date**: Type: dateTime  (Hidden)  , Summarized by: none
- **Año**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **NroMes**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Mes**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **NroTrimestre**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Trimestre**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **Día**: Type: int64  (Hidden)  (Calculated) , Summarized by: none

### Partitions:

- **Name**: LocalDateTable_f05f7ddd-2f16-41de-a870-85a6c9becf36, **Mode**: import, **Expression**: 
```
Calendar(Date(Year(MIN('TAB_RESUMEN'[FECHA])), 1, 1), Date(Year(MAX('TAB_RESUMEN'[FECHA])), 12, 31))
```


## Table: TAB_SUPERVISORES

### Columns:

- **ID_SUP**: Type: int64   , Summarized by: none
- **SUPERVISORES**: Type: string   , Summarized by: none

### Partitions:

- **Name**: TAB_SUPERVISORES, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    TAB_SUPERVISORES_Table = Origen{[Item="TAB_SUPERVISORES",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(TAB_SUPERVISORES_Table,{{"ID_SUP", Int64.Type}, {"SUPERVISORES", type text}})
in
    #"Tipo cambiado"
```


## Table: TAB_CLIENTE

### Columns:

- **ID_CLI**: Type: int64   , Summarized by: none
- **CLIENTE**: Type: string   , Summarized by: none
- **TOTAL ACTUAL**: Type: int64   , Summarized by: none

### Partitions:

- **Name**: TAB_CLIENTE, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    TAB_CLIENTE_Table = Origen{[Item="TAB_CLIENTE",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(TAB_CLIENTE_Table,{{"ID_CLI", Int64.Type}, {"CLIENTE", type text}, {"TOTAL ACTUAL", Int64.Type}})
in
    #"Tipo cambiado"
```


## Table: tab_01

### Columns:

- **Columna1**: Type: dateTime   , Summarized by: none
- **STOCK**: Type: int64   , Summarized by: sum
- **PROGRAMADOS**: Type: int64   , Summarized by: sum
- **ATENDIDOS**: Type: int64   , Summarized by: sum
- **NO ATENDIDOS**: Type: int64   , Summarized by: sum

### Partitions:

- **Name**: tab_01, **Mode**: import, **Expression**: 
```
let
    Origen = Excel.Workbook(File.Contents("D:\A6\2025\01.xlsx"), null, true),
    tab_01_Table = Origen{[Item="tab_01",Kind="Table"]}[Data],
    #"Tipo cambiado" = Table.TransformColumnTypes(tab_01_Table,{{"Columna1", type date}, {"STOCK", Int64.Type}, {"PROGRAMADOS", Int64.Type}, {"ATENDIDOS", Int64.Type}, {"NO ATENDIDOS", Int64.Type}})
in
    #"Tipo cambiado"
```


## Table: LocalDateTable_447d0df7-e1db-45d5-833e-c807b4b42272

### Columns:

- **Date**: Type: dateTime  (Hidden)  , Summarized by: none
- **Año**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **NroMes**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Mes**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **NroTrimestre**: Type: int64  (Hidden)  (Calculated) , Summarized by: none
- **Trimestre**: Type: string  (Hidden)  (Calculated) , Summarized by: none
- **Día**: Type: int64  (Hidden)  (Calculated) , Summarized by: none

### Partitions:

- **Name**: LocalDateTable_447d0df7-e1db-45d5-833e-c807b4b42272, **Mode**: import, **Expression**: 
```
Calendar(Date(Year(MIN('tab_01'[Columna1])), 1, 1), Date(Year(MAX('tab_01'[Columna1])), 12, 31))
```



## Relationships

- Relationship: **442f2006-2dad-4ac7-955d-a84a769aa4ce**  From: **TAB_RESUMEN** (column: **FECHA**) To: **LocalDateTable_f05f7ddd-2f16-41de-a870-85a6c9becf36** (column: **Date**)
- Relationship: **AutoDetected_9705aeb8-b2a8-47d6-b918-9dbcf8fe9d10**  From: **TAB_RESUMEN** (column: **ID_CAT**) To: **TAB_CATEGORIA** (column: **ID_CAT**)
- Relationship: **AutoDetected_2c0a9554-7837-4f62-861f-a08aeec6531e**  From: **TAB_RESUMEN** (column: **ID_OBS**) To: **TAB_OBSERVACION** (column: **ID_OBS**)
- Relationship: **AutoDetected_6b67f819-a966-4530-8f41-0c228f114a59**  From: **TAB_RESUMEN** (column: **ID_CLI**) To: **TAB_CLIENTE** (column: **ID_CLI**)
- Relationship: **AutoDetected_acbdf11e-9e8b-4a6d-9fd1-23dfbec69c7a**  From: **TAB_RESUMEN** (column: **ID_SUP**) To: **TAB_SUPERVISORES** (column: **ID_SUP**)
- Relationship: **1d5b26bb-d0e1-4379-ad9b-d2fe89b6f5c7**  From: **tab_01** (column: **Columna1**) To: **LocalDateTable_447d0df7-e1db-45d5-833e-c807b4b42272** (column: **Date**)
