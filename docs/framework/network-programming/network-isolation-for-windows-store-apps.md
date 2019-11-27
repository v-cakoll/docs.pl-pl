---
title: Izolacja sieci dla aplikacji ze sklepu Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 34b8865781079f45a68d3dd1aab7fbd66c703d50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447422"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolacja sieci dla aplikacji ze sklepu Windows Store
Klasy w przestrzeniach nazw <xref:System.Net>, <xref:System.Net.Http>i <xref:System.Net.Http.Headers> mogą służyć do tworzenia aplikacji do sklepu Windows lub aplikacji klasycznych. W przypadku użycia w aplikacji ze sklepu Windows na klasy w tych obszarach nazw ma wpływ izolacja sieci, która jest częścią modelu zabezpieczeń aplikacji używanego przez [!INCLUDE[win8](../../../includes/win8-md.md)]. Odpowiednie możliwości sieci muszą być włączone w manifeście aplikacji dla aplikacji ze sklepu Windows dla systemu, aby umożliwić dostęp do sieci.  
  
## <a name="checklist-for-network-isolation"></a>Lista kontrolna dotycząca izolacji sieci  
 Użyj tej listy kontrolnej, aby upewnić się, że izolacja sieciowa jest skonfigurowana dla aplikacji ze sklepu Windows.  
  
1. Określ kierunek żądań dostępu do sieci wymaganych przez aplikację. Może to być wychodzące żądania inicjowane przez klienta lub przychodzące żądania, które może być połączeniem obu tych typów żądań sieciowych.  
  
2. Określ typ zasobów sieciowych, z którymi będzie komunikować się aplikacja. Aplikacja może wymagać komunikacji z zaufanymi zasobami w sieci domowej lub służbowej. Aplikacja może wymagać komunikacji z zasobami w Internecie. Aplikacja może potrzebować dostępu do obu typów zasobów sieciowych.  
  
3. Skonfiguruj minimalną wymaganą izolację sieciową w manifeście aplikacji.  
  
4. Wdróż i uruchom aplikację w celu przetestowania jej przy użyciu narzędzi do izolacji sieciowej dostępnych do rozwiązywania problemów.  
  
 Aby uzyskać bardziej szczegółowe informacje na temat konfigurowania możliwości sieci i narzędzi do izolacji w celu rozwiązywania problemów z izolacją sieci, zobacz [jak skonfigurować możliwości izolacji sieci](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) w dokumentacji dla deweloperów Sklepu Windows 8. x.
  
## <a name="see-also"></a>Zobacz także

- [Łączenie z usługą sieci Web](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Wskazówki i Lista kontrolna izolacji sieci](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Szybki Start: Łączenie przy użyciu HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Jak używać programów obsługi HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Jak zabezpieczyć połączenia HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Przykład HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
