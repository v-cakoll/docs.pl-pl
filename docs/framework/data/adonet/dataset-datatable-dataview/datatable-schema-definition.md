---
title: Definicja schematu elementu DataTable
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 60e7f6a13bd7fd10398d300690bd73c3abc0d700
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552156"
---
# <a name="datatable-schema-definition"></a>Definicja schematu elementu DataTable
Schemat lub struktura tabeli jest reprezentowany przez kolumn i ograniczeń. Należy zdefiniować schemat <xref:System.Data.DataTable> przy użyciu <xref:System.Data.DataColumn> obiektów także <xref:System.Data.ForeignKeyConstraint> i <xref:System.Data.UniqueConstraint> obiektów. Kolumny w tabeli można zamapować do kolumny w źródle danych, zawierać obliczone wartości w wyrażeniach, automatycznie zwiększyć ich wartości lub wartości klucza podstawowego.  
  
 Odwołania według nazwy kolumny, relacje i ograniczenia w tabeli jest rozróżniana wielkość liter. W tabeli, które mają taką samą nazwę, ale które różnią się w przypadku w związku z tym może istnieć co najmniej dwóch kolumn, relacji lub ograniczenia. Na przykład można mieć **Col1** i **col1**. W takich jak przypadek, odwołanie do jednej z kolumn według nazwy musi być zgodny wielkość liter nazwy kolumny; w przeciwnym razie jest zgłaszany wyjątek. Na przykład jeśli tabela **myTable** zawiera kolumny **Col1** i **col1**, czy odwołanie **Col1** według nazwy, jako  **myTable.Columns["Col1"]**, i **col1** jako **myTable.Columns["col1"]**. Podjęto próbę odwoływać się do jednej z kolumn jako **myTable.Columns["COL1"]** wygeneruje wyjątek.  
  
 Zasada uwzględnianie wielkości liter nie ma zastosowania, jeśli tylko jednej kolumny, relacji lub ograniczenie o określonej nazwie istnieje. Oznacza to jeśli nie kolumny, relacji lub obiektu ograniczeń w tabeli jest zgodna z nazwą tej konkretnej kolumny, relacji lub obiektu ograniczeń, według nazwy przy użyciu każdy przypadek może odwoływać się obiekt i jest zgłaszany żaden wyjątek. Na przykład, jeśli tabela ma tylko **Col1**, możesz odwoływać się za pomocą **Moje. Kolumny ["COL1"]**.  
  
> [!NOTE]
>  <xref:System.Data.DataTable.CaseSensitive%2A> Właściwość **DataTable** nie wpływa na to zachowanie. **CaseSensitive** właściwość ma zastosowanie do danych w tabeli i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczeń i tak dalej, ale nie do odwołania do kolumny, relacje i ograniczenia.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie kolumn do elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-columns-to-a-datatable.md)  
 W tym artykule opisano sposób definiowania kolumn tabeli przy użyciu **DataColumn** obiektów.  
  
 [Tworzenie kolumn wyrażeń](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-expression-columns.md)  
 Wyjaśnia sposób, w jaki **wyrażenie** właściwość kolumny może służyć do obliczania wartości na podstawie wartości z innych kolumn w wierszu.  
  
 [Tworzenie kolumn typu AutoIncrement](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)  
 W tym artykule opisano, jak można ustawić kolumny, aby automatycznie Zwiększ wartości liczbowych, aby upewnić się, wartością unikatową kolumnę na wiersz.  
  
 [Definiowanie kluczy podstawowych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)  
 Opisuje sposób określenia klucza podstawowego w tabeli z jednej lub wielu **DataColumn** obiektów.  
  
 [Ograniczenia elementu DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)  
 W tym artykule opisano sposób definiowania foreign key i ograniczenia unikatowe dla kolumn w tabeli.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
