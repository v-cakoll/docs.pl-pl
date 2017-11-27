---
title: "Porady: Generowanie modelu obiektu jako zewnętrzny plik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ca0824fd7f5c4145205d28cae4b6d262ae49cbf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Porady: Generowanie modelu obiektu jako zewnętrzny plik
Jako alternatywę do mapowania na podstawie atrybutów można wygenerować modelu obiektu jako plik XML za pomocą narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SqlMetal.exe (narzędzie generowania kodu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md). Za pomocą zewnętrznego pliku mapowania XML, możesz zaśmiecać w kodzie. Zachowanie można również zmienić, modyfikując plik zewnętrzny bez konieczności ponownego kompilowania plików binarnych aplikacji. Aby uzyskać więcej informacji, zobacz [zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje generowania pliku mapowania zewnętrznych.  
  
## <a name="example"></a>Przykład  
 Polecenie generuje plik mapowania zewnętrznych z przykładowej bazy danych Northwind.  
  
```  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Przykład  
 Poniższy fragment pliku mapowania zewnętrznych zawiera mapowania dla tabeli klientów w bazie danych Northwind. Ten fragment został wygenerowany, wykonując SQLMetal z **/map** opcji.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Database xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" Name="northwnd">  
  <Table Name="Customers">  
    <Type Name=".Customer">  
      <Column Name="CustomerID" Member="CustomerID" Storage="_CustomerID" DbType="NChar(5) NOT NULL" CanBeNull="False" IsPrimaryKey="True" />  
      <Column Name="CompanyName" Member="CompanyName" Storage="_CompanyName" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Member="ContactName" Storage="_ContactName" DbType="NVarChar(30)" />  
      <Column Name="ContactTitle" Member="ContactTitle" Storage="_ContactTitle" DbType="NVarChar(30)" />  
      <Column Name="Address" Member="Address" Storage="_Address" DbType="NVarChar(60)" />  
      <Column Name="City" Member="City" Storage="_City" DbType="NVarChar(15)" />  
      <Column Name="Region" Member="Region" Storage="_Region" DbType="NVarChar(15)" />  
      <Column Name="PostalCode" Member="PostalCode" Storage="_PostalCode" DbType="NVarChar(10)" />  
      <Column Name="Country" Member="Country" Storage="_Country" DbType="NVarChar(15)" />  
      <Column Name="Phone" Member="Phone" Storage="_Phone" DbType="NVarChar(24)" />  
      <Column Name="Fax" Member="Fax" Storage="_Fax" DbType="NVarChar(24)" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" Storage="_CustomerCustomerDemos" ThisKey="CustomerID" OtherTable="CustomerCustomerDemo" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" Storage="_Orders" ThisKey="CustomerID" OtherTable="Orders" OtherKey="CustomerID" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie modelu obiektów](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapowanie zewnętrznych](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [Porady: Generowanie modelu obiektów w Visual Basic lub C#](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
