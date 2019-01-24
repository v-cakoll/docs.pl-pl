---
title: Omówienie modelu fabryki
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: b45e73dd21cad1381f58b578a19c39a1d89e8c3c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510043"
---
# <a name="factory-model-overview"></a>Omówienie modelu fabryki
ADO.NET w wersji 2.0 wprowadzono nowe klasy bazowe w <xref:System.Data.Common> przestrzeni nazw. Klasy bazowe są abstrakcyjne, co oznacza, że ich nie można bezpośrednio utworzyć wystąpienia. Obejmują one <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, i <xref:System.Data.Common.DbDataAdapter> i są udostępniane przez dostawcę danych .NET Framework, takich jak <xref:System.Data.SqlClient> i <xref:System.Data.OleDb>. Dodawanie klas bazowych upraszcza dodano funkcję dostawcy danych .NET Framework bez konieczności tworzenia nowych interfejsów.  
  
 ADO.NET w wersji 2.0 wprowadzono również abstrakcyjnych klas bazowych, które umożliwiają deweloperom pisanie kodu dostępu do danych typu ogólnego, które nie są zależne od dostawcy danych specyficznych dla.  
  
## <a name="the-factory-design-pattern"></a>Wzorzec projektowy fabryki  
 Model programowania do pisania kodu niezależnych od dostawcy opiera się na korzystanie z "fabrycznej" wzorcu projektowym używający jednego interfejsu API do baz danych programu access w wielu dostawców. Ten wzorzec jest aptly o nazwie, ponieważ odwołuje się do obiektu wyspecjalizowane jedynie, aby utworzyć inne obiekty, podobnie jak fabrykę rzeczywistych. Aby uzyskać bardziej szczegółowy opis wzorzec projektowy fabryki, zobacz [pisanie ogólne dane dostępu kodu dla programu ASP.NET 2.0 i ADO.NET w wersji 2.0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 Począwszy od wersji 2.0 programu ADO.NET, <xref:System.Data.Common.DbProviderFactories> klasa udostępnia `static` (lub `Shared` w języku Visual Basic) metody tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpienia. Wystąpienie zwraca poprawne silnie typizowany obiekt na podstawie informacji o dostawcy i parametry połączenia, podany w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- [Uzyskiwanie DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand i DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
