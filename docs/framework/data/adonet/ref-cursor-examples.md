---
title: Przykłady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 24830452e6d1ab11605ffa88a925fbc55c80b9bf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794710"
---
# <a name="ref-cursor-examples"></a>Przykłady REF CURSOR
Przykłady kursora REF składają się z trzech następujących przykładów Visual Basic firmy Microsoft, które demonstrują korzystanie z kursorów REF.  
  
|Przykład|Opis|  
|------------|-----------------|  
|[Parametry kursora REF CURSOR w OracleDataReader](ref-cursor-parameters-in-an-oracledatareader.md)|W tym przykładzie wykonywana jest procedura składowana PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](retrieving-data-from-multiple-ref-cursors.md)|W tym przykładzie wykonywana jest procedura składowana PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.|  
|[Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](filling-a-dataset-using-one-or-more-ref-cursors.md)|Ten przykład wykonuje procedurę składowaną pl/SQL, która zwraca dwa parametry kursora ref, i wypełnia <xref:System.Data.DataSet> z zwracanymi wierszami.|  
  
 Aby użyć tych przykładów, może być konieczne utworzenie tabel Oracle i utworzenie pakietu PL/SQL i treści pakietu.  
  
## <a name="creating-the-oracle-tables"></a>Tworzenie tabel Oracle  
 W tych przykładach użyto tabel, które są zdefiniowane w schemacie programu Oracle Scott/Tiger. Schemat programu Oracle Scott/Tiger jest dołączony do większości instalacji programu Oracle. Jeśli ten schemat nie istnieje, możesz użyć pliku poleceń SQL w {OracleHome} \rdbms\admin\scott.SQL, aby utworzyć tabele i indeksy używane przez te przykłady.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Tworzenie pakietu Oracle i treści pakietu  
 Poniższe przykłady wymagają pakietu PL/SQL i treści pakietu na serwerze. Utwórz następujący pakiet Oracle na serwerze Oracle.  
  
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
  
 Utwórz na serwerze Oracle następującą treść pakietu Oracle.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Oracle REF CURSOR](oracle-ref-cursors.md)
- [Omówienie ADO.NET](ado-net-overview.md)
