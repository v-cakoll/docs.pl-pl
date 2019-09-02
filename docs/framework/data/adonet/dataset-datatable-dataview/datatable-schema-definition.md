---
title: Definicja schematu elementu DataTable
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 0d2609801da3bc336c54d32068246027cfd6d3aa
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204993"
---
# <a name="datatable-schema-definition"></a>Definicja schematu elementu DataTable
Schemat lub struktura tabeli jest reprezentowana przez kolumny i ograniczenia. <xref:System.Data.DataTable> Zdefiniuj schemat <xref:System.Data.DataColumn> obiektów, <xref:System.Data.ForeignKeyConstraint> a także obiektów i <xref:System.Data.UniqueConstraint> . Kolumny w tabeli mogą być mapowane na kolumny w źródle danych, zawierają wartości obliczeniowe z wyrażeń, automatycznie zwiększają ich wartości lub zawierają wartości klucza podstawowego.  
  
 Odwołania według nazwy do kolumn, relacji i ograniczeń w tabeli są rozróżniane wielkości liter. Co najmniej dwie kolumny, relacje lub ograniczenia mogą istnieć w tabeli, która ma taką samą nazwę, ale różni się w przypadku. Na przykład można mieć **Kol1** i **Kol1**. W takim przypadku odwołanie do jednej z kolumn według nazwy musi być dokładnie zgodne z wielkością liter w nazwie kolumny; w przeciwnym razie zgłaszany jest wyjątek. Na przykład jeśli tabela **MyTable** zawiera kolumny **Kol1** i **Kol1**, należy odwołać się do **Kol1** według nazwy jako **MyTable. Columns ["Kol1"]** i **Kol1** jako **MyTable. Columns ["Kol1"]** . Próba odwoływania się do jednej z kolumn jako **MyTable. kolumny ["Kol1"]** spowodują wygenerowanie wyjątku.  
  
 Reguła uwzględniania wielkości liter nie ma zastosowania, jeśli istnieje tylko jedna kolumna, relacja lub ograniczenie o określonej nazwie. Oznacza to, że jeśli żadna inna kolumna, relacja lub obiekt ograniczenia w tabeli nie pasuje do nazwy tej konkretnej kolumny, relacji lub obiektu ograniczenia, można odwoływać się do obiektu według nazwy przy użyciu dowolnego przypadku, a żaden wyjątek nie jest zgłaszany. Na przykład jeśli tabela zawiera tylko **Kol1**, można odwoływać się do niej przy użyciu **My. Kolumny ["KOL1"]** .  
  
> [!NOTE]
> Właściwość elementu DataTable nie ma wpływu na to zachowanie. <xref:System.Data.DataTable.CaseSensitive%2A> Właściwość **CaseSensitive** ma zastosowanie do danych w tabeli i ma wpływ na sortowanie, wyszukiwanie, filtrowanie, wymuszanie ograniczeń itd., ale nie do odwołań do kolumn, relacji i ograniczeń.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Dodawanie kolumn do elementu DataTable](adding-columns-to-a-datatable.md)  
 Opisuje sposób definiowania kolumn tabeli przy użyciu obiektów DataColumn .  
  
 [Tworzenie kolumn wyrażeń](creating-expression-columns.md)  
 Wyjaśnia, w jaki sposób Właściwość **Expression** kolumny może służyć do obliczania wartości na podstawie wartości z innych kolumn w wierszu.  
  
 [Tworzenie kolumn typu AutoIncrement](creating-autoincrement-columns.md)  
 Opisuje, w jaki sposób można ustawić kolumnę, aby automatycznie zwiększać wartości liczbowe, aby zapewnić unikatową wartość kolumny dla każdego wiersza.  
  
 [Definiowanie kluczy podstawowych](defining-primary-keys.md)  
 Opisuje sposób określania klucza podstawowego tabeli z co najmniej jednego obiektu DataColumn.  
  
 [Ograniczenia elementu DataTable](datatable-constraints.md)  
 Opisuje sposób definiowania kluczy obcych i unikatowych ograniczeń dla kolumn w tabeli.  
  
## <a name="see-also"></a>Zobacz także

- [Elementy DataTable](datatables.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
