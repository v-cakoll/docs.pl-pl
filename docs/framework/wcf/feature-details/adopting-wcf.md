---
title: Adoptowanie programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: bcd6543e6cd47dc723b308acebec6f492fa14fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="adopting-windows-communication-foundation"></a>Adoptowanie programu Windows Communication Foundation
Można użyć Windows Communication Foundation (WCF) dla nowych aplikacji podczas kontynuowanie zachować istniejące aplikacje opracowane za pomocą programu ASP.NET. Ponieważ WCF ma być najbardziej odpowiednim rozwiązaniem ułatwiające komunikacji dla aplikacji skompilowanej za pomocą programu .NET Framework w jakimkolwiek scenariuszu, może służyć jako standardowe narzędzia do rozwiązywania szerokiej gamy problemów łączności oprogramowania w taki sposób, że ASP.NET Nie można wykonać.  
  
 Nowe aplikacje WCF można wdrożyć na tym samym maszynach jako istniejących usług sieci Web ASP.NET. Istniejące usługi sieci Web ASP.NET korzystania z wersji programu .NET Framework, przed w wersji 2.0, można użyć narzędzie rejestracji programu ASP.NET usług IIS do selektywnie wdrożenia programu .NET Framework 2.0 do aplikacji usług IIS, w których są nowe aplikacje WCF, ma być obsługiwana. Tego narzędzia jest udokumentowany na [narzędzie rejestracji programu ASP.NET usług IIS (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), i ma wbudowany interfejsu użytkownika, w konsoli zarządzania usług IIS 6.0.  
  
 Usługi WCF może służyć do dodawania nowych funkcji do istniejącej usługi sieci Web ASP.NET przez dodanie skonfigurowanego do uruchamiania w trybie zgodności ASP.NET do istniejącej aplikacji usługi sieci Web ASP.NET w usługach IIS usługi WCF. Ze względu na tryb zgodności ASP.NET, kod dla nowych usług WCF można uzyskać dostęp i zaktualizować przy użyciu tego samego informacji o stanie aplikacji jako istniejącego kodu platformy ASP.NET, <xref:System.Web.HttpContext> klasy. Aplikacje mogą również współużytkować tego samego biblioteki klas.  
  
 Klienci WCF za pomocą usług sieci Web ASP.NET. Usługi WCF, które są skonfigurowane przy użyciu <xref:System.ServiceModel.BasicHttpBinding> mogą być używane przez klientów usługi sieci Web ASP.NET. Usługi sieci Web ASP.NET mogą współistnieć z aplikacjami usługi WCF i WCF nawet służy do dodawania funkcji do istniejącej usługi sieci Web ASP.NET. Możliwość skorzystania z tych sposobów, w których usługi WCF i platformy ASP.NET w sieci Web mogą być używane razem, można przeprowadzić migrację usług sieci Web ASP.NET do programu WCF tylko wtedy, gdy jest to wymagane funkcje, które są udostępniane przez usługi WCF i nie sieci Web ASP.NET.  
  
 Nawet w kilku przypadkach, gdy jest to konieczne należy rozważyć Migrowanie kod z jednego technologii do innego jest rzadko właściwe podejście. Przyczyna przyjęcie nowych technologii jest aby spełnić nowe wymagania, które nie mogą być spełnione wraz z technologią wcześniej, i w takim przypadku jest poprawne pierwsze, należy zaprojektować nowe rozwiązanie spełnia nowo rozszerzony zestaw wymagań. Nowy projekt korzyści z środowiska z istniejącym systemem i mądry uzyskane od została zaprojektowana w tym systemie. Nowy projekt można również użyć pełnego zestawu funkcji nowych technologii niż odtwarzanie starego projektu na nowej platformie. Po prototypowania kluczowe elementy nowy projekt staje się łatwiejsze do ponownego użycia kodu z istniejącego systemu w nowym.  
  
 Kilka przykładów w przypadku, gdy eksportowanie z usług sieci Web ASP.NET do programu WCF jest właściwym rozwiązaniem, poniższa sekcja zawiera niektóre wskazówki dotyczące postępowania. Brak porady na temat migracji usług i sposobu migracji klientów.  
  
 Do ukończenia analizy dotyczące sposobu przeprowadzenia migracji istniejącej usługi sieci Web ASP.NET do programu WCF zobacz [usług sieci Web ASP.NET i Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). W tej sekcji opisano sposobu wdrażania usługi WCF zgodne z metadanych dla Ciebie usługi sieci Web ASP.NET i jak przeprowadzić migrację kodu usługi i klienta sieci Web ASP.NET do programu WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Instrukcje: migrowanie kodu usługi internetowej opartej na platformie ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Instrukcje: migrowanie kodu klienta usługi internetowej na platformie ASP.NET do programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)
