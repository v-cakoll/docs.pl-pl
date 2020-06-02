---
title: Dodawanie kolumn do elementu DataTable
description: Element DataTable zawiera obiekty DataColumn, do których odwołują się właściwości Columns tabeli. Użyj tego przykładowego kodu, aby dodać kolumny do tabeli w ADO.NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 9d6d21696acd7a6b63cfd6d2ea7e906ec2acd7c9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286950"
---
# <a name="adding-columns-to-a-datatable"></a>Dodawanie kolumn do elementu DataTable
A <xref:System.Data.DataTable> zawiera kolekcję obiektów, <xref:System.Data.DataColumn> do których odwołuje się Właściwość **kolumn** tabeli. Ta kolekcja kolumn, wraz z wszelkimi ograniczeniami, definiuje schemat, czyli strukturę tabeli.  
  
 Tworzysz obiekty **DataColumn** w tabeli przy użyciu konstruktora **DataColumn** lub wywołując metodę **Add** właściwości **Columns** tabeli, która jest <xref:System.Data.DataColumnCollection> . Metoda **Add** akceptuje opcjonalne argumenty **ColumnName**, **DataType**i **Expression** i tworzy nową **kolumnę DataColumn** jako element członkowski kolekcji. Akceptuje również istniejący obiekt **DataColumn** i dodaje go do kolekcji i zwraca odwołanie do dodanej **kolumny** , jeśli jest to wymagane. Ponieważ obiekty **DataTable** nie są specyficzne dla żadnego źródła danych, typy .NET Framework są używane podczas określania typu danych w **kolumnie DataColumn**.  
  
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
> Jeśli nie podano nazwy kolumny dla kolumny, kolumna otrzymuje przyrostową domyślną nazwę kolumny*N,* rozpoczynając od "Kolumna1", gdy zostanie dodana do elementu **DataColumnCollection**. Zalecamy uniknięcie konwencji nazewnictwa "Column*N*" w przypadku podania nazwy kolumny, ponieważ dostarczona nazwa może powodować konflikt z istniejącą domyślną nazwą kolumny w elemencie **DataColumnCollection**. Jeśli podana nazwa już istnieje, zgłaszany jest wyjątek.  
  
 Jeśli używasz programu <xref:System.Xml.Linq.XElement> jako elementu <xref:System.Data.DataColumn.DataType%2A> <xref:System.Data.DataColumn> w <xref:System.Data.DataTable> , serializacja XML nie będzie działała podczas odczytywania danych. Na przykład jeśli piszesz a przy <xref:System.Xml.XmlDocument> użyciu `DataTable.WriteXml` metody, po serializacji do kodu XML istnieje dodatkowy węzeł nadrzędny w obiekcie <xref:System.Xml.Linq.XElement> . Aby obejść ten problem, użyj <xref:System.Data.SqlTypes.SqlXml> typu zamiast <xref:System.Xml.Linq.XElement> . `ReadXml`i `WriteXml` działają poprawnie z <xref:System.Data.SqlTypes.SqlXml> .  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [Definicja schematu elementu DataTable](datatable-schema-definition.md)
- [Elementy DataTable](datatables.md)
- [Omówienie ADO.NET](../ado-net-overview.md)
