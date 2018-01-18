---
title: "Omówienie modelu fabryki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a><span data-ttu-id="3ef37-102">Omówienie modelu fabryki</span><span class="sxs-lookup"><span data-stu-id="3ef37-102">Factory Model Overview</span></span>
<span data-ttu-id="3ef37-103">ADO.NET 2.0 wprowadzono nowe klasy podstawowej w <xref:System.Data.Common> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ef37-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="3ef37-104">Klasy podstawowe są abstrakcyjnego, co oznacza, że ich nie można bezpośrednio utworzyć wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3ef37-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="3ef37-105">Obejmują one <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, i <xref:System.Data.Common.DbDataAdapter> i są współdzielone przez dostawców danych .NET Framework, takich jak <xref:System.Data.SqlClient> i <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="3ef37-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="3ef37-106">Dodawanie klas podstawowych upraszcza dodawania funkcji do dostawcy danych .NET Framework bez konieczności tworzenia nowych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="3ef37-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="3ef37-107">ADO.NET 2.0 wprowadzono również abstrakcyjnych klas podstawowych, które umożliwiają deweloperom pisanie kodu dostępu do danych typu ogólnego, który nie zależy od dostawcy określonych danych.</span><span class="sxs-lookup"><span data-stu-id="3ef37-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="3ef37-108">Wzorzec projektowy fabryki</span><span class="sxs-lookup"><span data-stu-id="3ef37-108">The Factory Design Pattern</span></span>  
 <span data-ttu-id="3ef37-109">Model programowania do pisania kodu niezależne od dostawcy opiera się na użycie wzorca projektowego "fabrycznej", który używa jednego interfejsu API baz danych programu access na wielu dostawców.</span><span class="sxs-lookup"><span data-stu-id="3ef37-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="3ef37-110">Ten wzorzec jest aptly o nazwie, ponieważ odwołuje się do obiektu specjalne jedynie, aby utworzyć inne obiekty, podobnie jak w fabryce rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="3ef37-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="3ef37-111">Bardziej szczegółowy opis wzorca projektowego fabryki, zobacz "[zapisywanie ogólnego kod dostępu do danych w programie ASP.NET 2.0 oraz ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" i "Ogólny kodowania z ADO.NET 2.0 Base klas i fabryki" [http:// MSDN.microsoft.com/library/default.asp?URL=/library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="3ef37-111">For a more detailed description of the factory design pattern, see "[Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" and "Generic Coding with the ADO.NET 2.0 Base Classes and Factories" [http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) on MSDN.</span></span>  
  
 <span data-ttu-id="3ef37-112">Począwszy od ADO.NET 2.0 <xref:System.Data.Common.DbProviderFactories> klasa udostępnia `static` (lub `Shared` w języku Visual Basic) metody tworzenia <xref:System.Data.Common.DbProviderFactory> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3ef37-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="3ef37-113">Wystąpienie zwraca prawidłowe silnie typizowany obiekt na podstawie informacji o dostawcy i ciąg połączenia podany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3ef37-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef37-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ef37-114">See Also</span></span>  
 [<span data-ttu-id="3ef37-115">Uzyskiwanie DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="3ef37-115">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [<span data-ttu-id="3ef37-116">DbConnection, DbCommand i DbException</span><span class="sxs-lookup"><span data-stu-id="3ef37-116">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [<span data-ttu-id="3ef37-117">Modyfikowanie danych za pomocą obiektu DbDataAdapter</span><span class="sxs-lookup"><span data-stu-id="3ef37-117">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="3ef37-118">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="3ef37-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
