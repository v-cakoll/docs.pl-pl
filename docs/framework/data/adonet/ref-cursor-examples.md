---
title: Przykłady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dc82648ff5a565c9b4d6fa593433ee1e22249d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149138"
---
# <a name="ref-cursor-examples"></a>Przykłady REF CURSOR
Przykłady kursora REF składają się z następujących trzech przykładów programu Microsoft Visual Basic, które demonstrują przy użyciu cursorów REF.  
  
|Sample|Opis|  
|------------|-----------------|  
|[Parametry kursora REF CURSOR w OracleDataReader](ref-cursor-parameters-in-an-oracledatareader.md)|W tym przykładzie wykonuje procedurę składowaną PL/SQL, która zwraca parametr <xref:System.Data.OracleClient.OracleDataReader>REF CURSOR i odczytuje wartość jako .|  
|[Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](retrieving-data-from-multiple-ref-cursors.md)|W tym przykładzie wykonuje procedurę składowaną PL/SQL, która zwraca dwa parametry KURSORA REF i odczytuje wartości za pomocą **czytnika OracleDataReader**.|  
|[Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](filling-a-dataset-using-one-or-more-ref-cursors.md)|W tym przykładzie wykonuje pl/SQL procedura składowana, która zwraca <xref:System.Data.DataSet> dwa parametry KURSOR REF i wypełnia wiersze, które są zwracane.|  
  
 Aby użyć tych przykładów, może być konieczne utworzenie tabel Oracle i należy utworzyć pakiet PL/SQL i treść pakietu.  
  
## <a name="creating-the-oracle-tables"></a>Tworzenie tabel Oracle  
 W tych przykładach użyto tabel zdefiniowanych w schemacie Oracle Scott/Tiger. Schemat Oracle Scott/Tiger jest dołączony do większości instalacji Oracle. Jeśli ten schemat nie istnieje, można użyć pliku poleceń SQL w {OracleHome}\rdbms\admin\scott.sql, aby utworzyć tabele i indeksy używane przez te przykłady.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Tworzenie pakietu Oracle i treści pakietów  
 Te przykłady wymagają następującego pakietu PL/SQL i treści pakietu na serwerze. Utwórz następujący pakiet Oracle na serwerze Oracle.  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
    TYPE T_CURSOR IS REF CURSOR;
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,
                               IO_CURSOR IN OUT T_CURSOR);
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/
```  
  
 Utwórz następującą treść pakietu Oracle na serwerze Oracle.  
  
```sql
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS
        V_CURSOR T_CURSOR;
    BEGIN
        IF N_EMPNO <> 0
        THEN  
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE
             OPEN V_CURSOR FOR
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME
                  FROM EMP, DEPT
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;
    END OPEN_ONE_CURSOR;
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS
        V_CURSOR1 T_CURSOR;
        V_CURSOR2 T_CURSOR;
    BEGIN
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;
        DEPTCURSOR := V_CURSOR2;
    END OPEN_TWO_CURSORS;
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a>Zobacz też

- [Oracle REF CURSOR](oracle-ref-cursors.md)
- [Omówienie ADO.NET](ado-net-overview.md)
