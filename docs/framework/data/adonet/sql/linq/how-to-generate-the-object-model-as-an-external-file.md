---
title: 'Instrukcje: Generowanie modelu obiektu jako pliku zewnętrznego'
ms.date: 03/30/2017
ms.assetid: 2496fa06-3df4-4ecb-86c4-70a49ea08565
ms.openlocfilehash: 915c02de55211efa24a4aa9f21ddc2c7e60fa41a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002743"
---
# <a name="how-to-generate-the-object-model-as-an-external-file"></a>Instrukcje: Generowanie modelu obiektu jako pliku zewnętrznego
Alternatywą dla mapowania opartego na atrybutach jest generowanie modelu obiektu jako zewnętrznego pliku XML przy użyciu narzędzia wiersza polecenia SQLMetal. Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md). Przy użyciu zewnętrznego pliku mapowania XML można zmniejszyć ilość bałaganu w kodzie. Możesz również zmienić zachowanie, modyfikując plik zewnętrzny bez ponownego kompilowania plików binarnych aplikacji. Aby uzyskać więcej informacji, zobacz [Mapowanie zewnętrzne](external-mapping.md).  
  
> [!NOTE]
> Object Relational Designer nie obsługuje generowania pliku mapowania zewnętrznego.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje zewnętrzny plik mapowania z przykładowej bazy danych Northwind.  
  
```console  
sqlmetal /server:myserver /database:northwind /map:externalfile.xml  
```  
  
## <a name="example"></a>Przykład  
 Poniższy fragment z zewnętrznego pliku mapowania przedstawia Mapowanie tabeli Customers w przykładowej bazie danych Northwind. Ten fragment został wygenerowany przez wykonanie SQLMetal z opcją **/map** .  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Mapowanie zewnętrzne](external-mapping.md)
- [Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
