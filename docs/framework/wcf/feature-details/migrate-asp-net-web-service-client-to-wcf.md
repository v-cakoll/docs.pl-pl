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
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Instrukcje: Migrowanie kodu klienta usługi sieci Web na platformie ASP.NET do programu Windows Communication Foundation
W poniższej procedurze opisano czynności, które muszą być zachowana w celu Migrowanie kodu klienta usługi sieci Web ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>Aby przeprowadzić migrację kodu klienta usługi sieci Web ASP.NET do programu WCF  
  
1.  Upewnij się, że o zaawansowany zestaw testów istnieje dla klienta.  
  
2.  Użyj programu Visual Studio 2005, aby uaktualnić aplikację klienta do .NET 2.0. Uruchom zestaw testów.  
  
3.  Usuń kod klienta ASP.NET z projektu klienta. Ten kod jest w modułach wygenerowany za pomocą narzędzia WSDL.exe.  
  
4.  Generowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodu klienta za pomocą [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Dodaj ten kod do projektu klienta i scalanie danych wyjściowych konfiguracji w pliku konfiguracji z istniejącego klienta.  
  
5.  Kompilowanie aplikacji. Napraw błędy kompilacji, zastępując odwołania do poprzedniego typy klientów platformy ASP.NET z odwołaniami do nowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typy klientów.  
  
6.  Uruchom zestaw testów.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: migrowanie kodu usługi internetowej opartej na platformie ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
