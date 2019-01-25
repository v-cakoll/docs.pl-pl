---
title: Przykłady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 00e1cd1b9c13514979ee22b32996d35e1bd1c3e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615351"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="b5c9a-102">Przykłady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b5c9a-102">REF CURSOR Examples</span></span>
<span data-ttu-id="b5c9a-103">Przykłady REF CURSOR składają się z następujące trzy przykłady języka Visual Basic, które przedstawiają, za pomocą kursora REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="b5c9a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5c9a-104">Sample</span></span>|<span data-ttu-id="b5c9a-105">Opis</span><span class="sxs-lookup"><span data-stu-id="b5c9a-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b5c9a-106">Parametry kursora REF CURSOR w OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="b5c9a-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="b5c9a-107">W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="b5c9a-108">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="b5c9a-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="b5c9a-109">W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca dwa parametry REF CURSOR, a następnie odczytuje wartości za pomocą **Element OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="b5c9a-110">Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b5c9a-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="b5c9a-111">W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca dwa parametry REF CURSOR i wypełnia <xref:System.Data.DataSet> wierszy, które są zwracane.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="b5c9a-112">Aby korzystać z tych przykładów, może być konieczne utworzenie tabel bazy danych Oracle i należy utworzyć pakiet PL/SQL i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="b5c9a-113">Tworzenie tabel Oracle</span><span class="sxs-lookup"><span data-stu-id="b5c9a-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="b5c9a-114">Te przykłady korzystanie z tabel, które są zdefiniowane w schemacie Oracle Scott/Tiger.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="b5c9a-115">Schemat bazy danych Oracle Scott/Tiger jest dołączana do większości instalacji programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="b5c9a-116">Jeśli w tym schemacie nie istnieje, możesz użyć pliku poleceń SQL w {OracleHome}\rdbms\admin\scott.sql tworzyć tabele i indeksy używane przez te przykłady.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="b5c9a-117">Tworzenie pakietu programu Oracle i ciało pakietu</span><span class="sxs-lookup"><span data-stu-id="b5c9a-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="b5c9a-118">Te przykłady wymagają następujących pakietów PL/SQL i treść pakietu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="b5c9a-119">Utwórz następujący pakiet oprogramowania Oracle na serwerze bazy danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="b5c9a-120">Utwórz następujące ciało pakietu oprogramowania Oracle na serwerze bazy danych Oracle.</span><span class="sxs-lookup"><span data-stu-id="b5c9a-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5c9a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5c9a-121">See also</span></span>
- [<span data-ttu-id="b5c9a-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="b5c9a-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [<span data-ttu-id="b5c9a-123">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b5c9a-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
