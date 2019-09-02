---
title: Dodawanie kolumn do elementu DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 105537a5fccef6de7266407c78cc915f8c5d8678
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204061"
---
# <a name="adding-columns-to-a-datatable"></a>Dodawanie kolumn do elementu DataTable
A <xref:System.Data.DataTable> zawiera<xref:System.Data.DataColumn> kolekcję obiektów, do których odwołuje się Właściwość **kolumn** tabeli. Ta kolekcja kolumn, wraz z wszelkimi ograniczeniami, definiuje schemat, czyli strukturę tabeli.  
  
 Tworzysz obiekty **DataColumn** w tabeli przy użyciu konstruktora DataColumn lub wywołując metodę **Add** właściwości Columns tabeli, która jest. <xref:System.Data.DataColumnCollection> Metoda **Add** akceptuje opcjonalne argumenty **ColumnName**, **DataType**i **Expression** i tworzy nową **kolumnę DataColumn** jako element członkowski kolekcji. Akceptuje również istniejący obiekt **DataColumn** i dodaje go do kolekcji i zwraca odwołanie do dodanej **kolumny** , jeśli jest to wymagane. Ponieważ obiekty **DataTable** nie są specyficzne dla żadnego źródła danych, typy .NET Framework są używane podczas określania typu danych w **kolumnie DataColumn**.  
  
 Poniższy przykład dodaje cztery kolumny do **elementu DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 W przykładzie należy zauważyć, że właściwości kolumny **CustId** są ustawione tak, aby nie zezwalały na wartości **DBNull** i ograniczać wartości jako unikatowe. Jednak w przypadku zdefiniowania kolumny **CustId** jako kolumny klucza podstawowego tabeli Właściwość **AllowDBNull** zostanie automatycznie ustawiona na **wartość false** , a właściwość **Unique** zostanie automatycznie ustawiona na **wartość true**. Aby uzyskać więcej informacji, zobacz [Definiowanie kluczy podstawowych](defining-primary-keys.md).  
  
> [!CAUTION]
> Jeśli nie podano nazwy kolumny dla kolumny, kolumna otrzymuje przyrostową domyślną nazwę kolumny*N,* rozpoczynając od "Kolumna1", gdy zostanie dodana do elementu DataColumnCollection. Zalecamy uniknięcie konwencji nazewnictwa "Column*N*" w przypadku podania nazwy kolumny, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą kolumny w elemencie DataColumnCollection. Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.  
  
 Jeśli używasz <xref:System.Xml.Linq.XElement> programu <xref:System.Data.DataColumn.DataType%2A> jako <xref:System.Data.DataColumn> elementu w<xref:System.Data.DataTable>, serializacja XML nie będzie działała podczas odczytywania danych. Na przykład jeśli piszesz a <xref:System.Xml.XmlDocument> przy `DataTable.WriteXml` użyciu metody, po serializacji do kodu XML istnieje <xref:System.Xml.Linq.XElement>dodatkowy węzeł nadrzędny w obiekcie. Aby obejść ten problem, użyj <xref:System.Data.SqlTypes.SqlXml> typu <xref:System.Xml.Linq.XElement>zamiast. `ReadXml`i `WriteXml` działają poprawnie z <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataTable](datatables.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
