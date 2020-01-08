---
title: Omówienie modelu fabryki
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: f344502453acbbb5c08e49b7c21a0f4e84a29ffa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348396"
---
# <a name="factory-model-overview"></a>Omówienie modelu fabryki
W ADO.NET 2,0 wprowadzono nowe klasy bazowe w przestrzeni nazw <xref:System.Data.Common>. Klasy podstawowe są abstrakcyjne, co oznacza, że nie można ich bezpośrednio utworzyć. Obejmują one <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>i <xref:System.Data.Common.DbDataAdapter> i są współdzielone przez dostawców danych .NET Framework, takich jak <xref:System.Data.SqlClient> i <xref:System.Data.OleDb>. Dodanie klas bazowych upraszcza Dodawanie funkcji do .NET Framework dostawców danych bez konieczności tworzenia nowych interfejsów.  
  
 W ADO.NET 2,0 wprowadzono również abstrakcyjne klasy podstawowe, które umożliwiają deweloperowi pisanie ogólnego kodu dostępu do danych, który nie zależy od określonego dostawcy danych.  
  
## <a name="the-factory-design-pattern"></a>Wzorzec projektowy fabryki  
 Model programowania służący do pisania kodu niezależnego od dostawcy jest oparty na użyciu wzorca projektowego "Factory", który używa jednego interfejsu API do uzyskiwania dostępu do baz danych przez wielu dostawców. Ten wzorzec to aptly o nazwie, ponieważ wywołuje użycie wyspecjalizowanego obiektu wyłącznie do tworzenia innych obiektów, podobnie jak w przypadku fabryki rzeczywistej. Aby zapoznać się z bardziej szczegółowym opisem wzorca projektowego, zobacz [pisanie ogólnego kodu dostępu do danych w ASP.NET 2,0 i ADO.NET 2,0](https://docs.microsoft.com/previous-versions/dotnet/articles/ms971499(v=msdn.10)).
  
 Począwszy od ADO.NET 2,0, Klasa <xref:System.Data.Common.DbProviderFactories> udostępnia metody `static` (lub `Shared` w Visual Basic) do tworzenia wystąpienia <xref:System.Data.Common.DbProviderFactory>. Wystąpienie zwraca poprawną silnie wpisaną obiekt na podstawie informacji o dostawcy i parametrów połączenia dostarczonych w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand i DbException](dbconnection-dbcommand-and-dbexception.md)
- [Modyfikowanie danych za pomocą obiektu DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Omówienie ADO.NET](ado-net-overview.md)
