---
title: Omówienie modelu fabryki
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 9efe6deb484b15cef08f616c154c893f5e8869e8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="factory-model-overview"></a>Omówienie modelu fabryki
ADO.NET 2.0 wprowadzono nowe klasy podstawowej w <xref:System.Data.Common> przestrzeni nazw. Klasy podstawowe są abstrakcyjnego, co oznacza, że ich nie można bezpośrednio utworzyć wystąpienia. Obejmują one <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, i <xref:System.Data.Common.DbDataAdapter> i są współdzielone przez dostawców danych .NET Framework, takich jak <xref:System.Data.SqlClient> i <xref:System.Data.OleDb>. Dodawanie klas podstawowych upraszcza dodawania funkcji do dostawcy danych .NET Framework bez konieczności tworzenia nowych interfejsów.  
  
 ADO.NET 2.0 wprowadzono również abstrakcyjnych klas podstawowych, które umożliwiają deweloperom pisanie kodu dostępu do danych typu ogólnego, który nie zależy od dostawcy określonych danych.  
  
## <a name="the-factory-design-pattern"></a>Wzorzec projektowy fabryki  
 Model programowania do pisania kodu niezależne od dostawcy opiera się na użycie wzorca projektowego "fabrycznej", który używa jednego interfejsu API baz danych programu access na wielu dostawców. Ten wzorzec jest aptly o nazwie, ponieważ odwołuje się do obiektu specjalne jedynie, aby utworzyć inne obiekty, podobnie jak w fabryce rzeczywistych. Bardziej szczegółowy opis wzorca projektowego fabryki, zobacz "[zapisywanie ogólnego kod dostępu do danych w programie ASP.NET 2.0 oraz ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" i "Ogólny kodowania z ADO.NET 2.0 Base klas i fabryki" [ http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp ](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) w witrynie MSDN.  
  
 Począwszy od ADO.NET 2.0 <xref:System.Data.Common.DbProviderFactories> klasa udostępnia `static` (lub `Shared` w języku Visual Basic) metody tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpienia. Wystąpienie zwraca prawidłowe silnie typizowany obiekt na podstawie informacji o dostawcy i ciąg połączenia podany w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
