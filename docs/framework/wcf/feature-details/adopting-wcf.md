---
title: Adoptowanie programu Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 5773d2687eb06cfc562dbe25fa9b94864b1b3a49
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565553"
---
# <a name="adopting-windows-communication-foundation"></a>Adoptowanie programu Windows Communication Foundation

Można użyć usługi Windows Communication Foundation (WCF) w nowych wdrożeniach, gdy przejdziesz dalej zachować istniejące aplikacje opracowane za pomocą programu ASP.NET. Ponieważ WCF mają być najbardziej odpowiednim wyborem w ułatwienia komunikacji przy użyciu aplikacji utworzonych za pomocą programu .NET Framework w każdym scenariuszu, może służyć jako standardowym narzędziem do rozwiązywania szerokiej gamy problemów łączności z oprogramowaniem w taki sposób, że program ASP.NET Nie można wykonać.

Nowe aplikacje WCF można wdrożyć w tej samej maszyny jako istniejących usług sieci Web platformy ASP.NET. Istniejących usług sieci Web platformy ASP.NET korzystania z wersji programu .NET Framework wcześniejszych niż 2.0, można użyć narzędzia rejestracji usług IIS platformy ASP.NET selektywnie wdrażania .NET Framework 2.0 do aplikacji usług IIS, w których mają być hostowane nowych aplikacji WCF. Tego narzędzia jest udokumentowany na [narzędzie rejestracji programu ASP.NET usług IIS (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687), i wbudowała interfejsu użytkownika w konsoli zarządzania usług IIS 6.0.

Usługi WCF, można dodać nowe funkcje do istniejących usług sieci Web platformy ASP.NET, dodając usług WCF skonfigurowane do uruchamiania w trybie zgodności w programie ASP.NET do istniejącej aplikacji usług sieci Web platformy ASP.NET w usługach IIS. Ze względu na tryb zgodności ASP.NET, kod dla nowych usług WCF można uzyskać dostęp i aktualizować tych samych informacji o stanie aplikacji jako istniejącego kodu platformy ASP.NET przy użyciu <xref:System.Web.HttpContext> klasy. Aplikacje można także udostępnić tej samej biblioteki klas.

Klienci WCF, mogą używać usług sieci Web platformy ASP.NET. Usługi WCF, które są skonfigurowane przy użyciu <xref:System.ServiceModel.BasicHttpBinding> mogą być używane przez klientów usługi sieci Web platformy ASP.NET. Usługi sieci Web platformy ASP.NET mogą współistnieć z funkcją aplikacji WCF i WCF nawet służy do dodawania funkcji do istniejących usług sieci Web platformy ASP.NET. Biorąc pod uwagę wszystkie z następujących sposobów, w których usługi WCF i platformy ASP.NET w sieci Web mogą być używane razem, można przeprowadzić migrację usług sieci Web platformy ASP.NET do programu WCF, tylko wtedy, gdy potrzebujesz funkcji, które są dostarczane przez usługi WCF i nie sieci Web platformy ASP.NET.

Nawet w nielicznych przypadkach, gdzie jest to konieczne Migrowanie kodu technologia jednego do drugiego rzadko jest właściwe podejście. Uzasadnienie nowej technologii jest spełniać nowe wymagania, nie można spełnić przy użyciu starszej technologii, a w takim przypadku pierwsze poprawne, należy jest nowe rozwiązanie, aby spełnić nowo rozwinięte ustalony zbiór wymogów dotyczących projektowania. Nowe korzyści projektu z korzystania z istniejącego systemu i podczas uzyskanych od zaprojektowano tak, że system. Nowy projekt umożliwia również w pełni możliwości nowych technologii, a nie odtwarzanie starego projektu na nowej platformie. Po tworzenia prototypów kluczowe elementy nowy projekt staje się łatwiejsze do ponownego użycia kodu z istniejącego systemu w ramach nowego.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
