---
title: "Instrukcje: Migrowanie kodu klienta usługi sieci Web na platformie ASP.NET do programu Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baf43f2bfa2175062c57f73e45835c251ac5769e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="3653c-102">Instrukcje: Migrowanie kodu klienta usługi sieci Web na platformie ASP.NET do programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3653c-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="3653c-103">W poniższej procedurze opisano czynności, które muszą być zachowana w celu Migrowanie kodu klienta usługi sieci Web ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3653c-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3653c-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="3653c-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="3653c-105">Aby przeprowadzić migrację kodu klienta usługi sieci Web ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="3653c-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="3653c-106">Upewnij się, że o zaawansowany zestaw testów istnieje dla klienta.</span><span class="sxs-lookup"><span data-stu-id="3653c-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="3653c-107">Użyj programu Visual Studio 2005, aby uaktualnić aplikację klienta do .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3653c-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="3653c-108">Uruchom zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="3653c-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="3653c-109">Usuń kod klienta ASP.NET z projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="3653c-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="3653c-110">Ten kod jest w modułach wygenerowany za pomocą narzędzia WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="3653c-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="3653c-111">Generowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodu klienta za pomocą [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3653c-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3653c-112">Dodaj ten kod do projektu klienta i scalanie danych wyjściowych konfiguracji w pliku konfiguracji z istniejącego klienta.</span><span class="sxs-lookup"><span data-stu-id="3653c-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="3653c-113">Kompilowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3653c-113">Compile the application.</span></span> <span data-ttu-id="3653c-114">Napraw błędy kompilacji, zastępując odwołania do poprzedniego typy klientów platformy ASP.NET z odwołaniami do nowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typy klientów.</span><span class="sxs-lookup"><span data-stu-id="3653c-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="3653c-115">Uruchom zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="3653c-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3653c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3653c-116">See Also</span></span>  
 [<span data-ttu-id="3653c-117">Instrukcje: migrowanie kodu usługi internetowej opartej na platformie ASP.NET do programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3653c-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
