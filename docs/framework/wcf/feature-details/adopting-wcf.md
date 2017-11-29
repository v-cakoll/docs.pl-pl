---
title: Adoptowanie programu Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 15fc02882148054fe53534c75905f51cfffe68fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="adopting-windows-communication-foundation"></a>Adoptowanie programu Windows Communication Foundation
Możesz użyć [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dla nowych aplikacji, podczas gdy kontynuowanie zachować istniejące aplikacje opracowane za pomocą programu ASP.NET. Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest przeznaczonych do najbardziej odpowiedniego wybór ułatwiające komunikacji dla aplikacji skompilowanej za pomocą programu .NET Framework w jakimkolwiek scenariuszu, może służyć jako standardowe narzędzie do szerokiej gamy problemów łączności oprogramowania w sposób rozwiązywania Nie można tego programu ASP.NET.  
  
 Nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje można wdrażać na tej samej maszyny zgodnie z istniejącą witrynę sieci Web platformy ASP.NET z usług. Jeśli istniejących usług sieci Web ASP.NET, użyj wersji programu .NET Framework, przed w wersji 2.0, a następnie można użyć narzędzia rejestracji ASP.NET usług IIS selektywnie wdrażania programu .NET Framework 2.0 do aplikacji usług IIS, w którym nowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje mają być obsługiwane. Tego narzędzia jest udokumentowany na [narzędzie rejestracji programu ASP.NET usług IIS (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), i ma wbudowany interfejsu użytkownika, w konsoli zarządzania usług IIS 6.0.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Służy do dodawania nowych funkcji do istniejącej usługi sieci Web ASP.NET, dodając [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi skonfigurowane do uruchamiania w trybie zgodności ASP.NET do istniejącej aplikacji usługi sieci Web ASP.NET w usługach IIS. Ze względu na tryb zgodności ASP.NET, kod dla nowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług można uzyskać dostęp i zaktualizować przy użyciu tego samego informacji o stanie aplikacji jako istniejącego kodu platformy ASP.NET, <xref:System.Web.HttpContext> klasy. Aplikacje mogą również współużytkować tego samego biblioteki klas.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Klienci mogą używać usług sieci Web ASP.NET. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]usługi, które są skonfigurowane przy użyciu <xref:System.ServiceModel.BasicHttpBinding> mogą być używane przez klientów usługi sieci Web ASP.NET. Usługi sieci Web ASP.NET mogą współistnieć z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nawet służy do dodawania funkcji do istniejącej usługi sieci Web ASP.NET. Podane wszystkich tych sposobów, w którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i usług sieci Web ASP.NET, które mogą być używane razem, może zajść potrzeba Migrowanie usług sieci Web ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tylko wtedy, gdy jest to wymagane funkcje, które są udostępniane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i nie usług sieci Web ASP.NET.  
  
 Nawet w kilku przypadkach, gdy jest to konieczne należy rozważyć Migrowanie kod z jednego technologii do innego jest rzadko właściwe podejście. Przyczyna przyjęcie nowych technologii jest aby spełnić nowe wymagania, które nie mogą być spełnione wraz z technologią wcześniej, i w takim przypadku jest poprawne pierwsze, należy zaprojektować nowe rozwiązanie spełnia nowo rozszerzony zestaw wymagań. Nowy projekt korzyści z środowiska z istniejącym systemem i mądry uzyskane od została zaprojektowana w tym systemie. Nowy projekt można również użyć pełnego zestawu funkcji nowych technologii niż odtwarzanie starego projektu na nowej platformie. Po prototypowania kluczowe elementy nowy projekt staje się łatwiejsze do ponownego użycia kodu z istniejącego systemu w nowym.  
  
 W kilku przypadkach, gdzie przenoszenie z sieci Web ASP.NET usług do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to prawidłowe rozwiązanie w poniższej sekcji przedstawiono pewne wskazówki dotyczące dalszego postępowania. Brak porady na temat migracji usług i sposobu migracji klientów.  
  
 Do ukończenia analizy dotyczące sposobu przeprowadzenia migracji istniejącej usługi sieci Web ASP.NET do programu WCF zobacz [usług sieci Web ASP.NET i Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). W tej sekcji opisano sposobu wdrażania usługi WCF zgodne z metadanych dla Ciebie usługi sieci Web ASP.NET i jak przeprowadzić migrację kodu usługi i klienta sieci Web ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Pobieranie metadanych i implementacji usługi zgodne](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Porady: Migrowanie kodu usługi sieci Web ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Porady: Migrowanie kodu klienta usługi sieci Web ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
