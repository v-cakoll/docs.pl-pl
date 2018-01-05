---
title: Definicja schematu tabeli DataTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e848a0fac5d41628d4d39f1771019eb870e6395b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-schema-definition"></a>Definicja schematu tabeli DataTable
Schemat lub struktura tabeli jest reprezentowana przez kolumn i ograniczeń. Zdefiniuj schemat <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataColumn> obiektów oraz <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów. Kolumn w tabeli można mapować do kolumn w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.  
  
 Odwołania według nazwy kolumny, relacji i ograniczeń w tabeli jest rozróżniana wielkość liter. W tabeli, które mają taką samą nazwę, ale które różnią się wielkością liter w związku z tym może istnieć co najmniej dwie kolumny, relacji lub ograniczenia. Na przykład można mieć **Col1** i **col1**. W przypadku, np. odwołanie do jednej z kolumn o nazwie muszą być zgodne wielkość liter nazwy kolumny; w przeciwnym razie jest zwracany wyjątek. Na przykład jeśli tabela **myTable** zawiera kolumny **Col1** i **col1**, czy odwołanie **Col1** według nazwy jako  **myTable.Columns["Col1"]**, i **col1** jako **myTable.Columns["col1"]**. Próby odwołania z kolumn jako **myTable.Columns["COL1"]** wygenerowanie wyjątku.  
  
 Reguła uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jednej kolumny, relacji lub ograniczenia o określonej nazwie istnieje. Oznacza to jeśli nie kolumny, relacji lub obiekt ograniczenie w tabeli jest zgodna z nazwą tej określonej kolumny, relacji lub ograniczenia obiektu, może odwoływać do obiektu o nazwie wszystkie wielkie i małe litery, a nie wyjątek. Na przykład, jeśli tabela zawiera tylko **Col1**, można odwoływać się za pomocą **Moje. Kolumny ["COL1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Właściwość **DataTable** nie ma wpływu na tego zachowania. **CaseSensitive** właściwość jest stosowana do danych w tabeli i wpływa na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczenia i tak dalej, ale nie do odwołania do kolumny, relacji i ograniczeń.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie kolumn do elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 Opisuje sposób definiowania kolumn tabeli, używając **DataColumn** obiektów.  
  
 [Tworzenie kolumn wyrażeń](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Wyjaśniono, jak **wyrażenie** właściwość kolumny może być używane do obliczania wartości na podstawie wartości z innych kolumn w wierszu.  
  
 [Tworzenie kolumn typu AutoIncrement](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 W tym artykule opisano, jak kolumny można ustawić na automatyczne zwiększenie wartości liczbowe, aby upewnić się, wartość unikatową kolumnę w wierszu.  
  
 [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Opisuje sposób określenia klucza podstawowego tabeli z jednej lub wielu **DataColumn** obiektów.  
  
 [Ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 Opisuje sposób zdefiniowania foreign key i ograniczenia unikalne dla kolumn w tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
