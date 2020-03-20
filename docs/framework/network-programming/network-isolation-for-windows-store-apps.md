---
title: Izolacja sieci dla aplikacji ze sklepu Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802164"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolacja sieci dla aplikacji ze sklepu Windows Store

Klasy w <xref:System.Net> <xref:System.Net.Http>programie <xref:System.Net.Http.Headers> , i przestrzenie nazw mogą być używane do tworzenia aplikacji ze Sklepu Windows lub aplikacji klasycznych. W przypadku użycia w aplikacji ze Sklepu Windows klasy w tych obszarach nazw podlegają izolacji sieci, która jest częścią modelu zabezpieczeń aplikacji używanego przez system Windows 8. Odpowiednie możliwości sieciowe muszą być włączone w manifeście aplikacji dla aplikacji ze Sklepu Windows, aby system zezwolił na dostęp do sieci.  
  
## <a name="checklist-for-network-isolation"></a>Lista kontrolna izolacji sieci  

Ta lista kontrolna umożliwia upewnienie się, że izolacja sieci jest skonfigurowana dla aplikacji ze Sklepu Windows.  
  
1. Określ kierunek żądań dostępu do sieci wymaganych przez aplikację. Może to być wychodzące żądania inicjowane przez klienta lub przychodzące niechciane żądania lub może to być kombinacja obu tych typów żądań sieciowych.  
  
2. Określ typ zasobów sieciowych, z którymi aplikacja będzie się komunikować. Aplikacja może wymagać komunikowania się z zaufanymi zasobami w sieci domowej lub służbowej. Aplikacja może wymagać komunikowania się z zasobami w Internecie. Aplikacja może wymagać dostępu do obu typów zasobów sieciowych.  
  
3. Skonfiguruj minimalne wymagane możliwości izolacji sieci w manifeście aplikacji.  
  
4. Wdrażanie i uruchamianie aplikacji w celu przetestowania jej przy użyciu narzędzi izolacji sieci dostarczonych do rozwiązywania problemów.  
  
Aby uzyskać bardziej szczegółowe informacje na temat konfigurowania funkcji sieci i narzędzi izolacji używanych do rozwiązywania problemów z izolacją sieci, zobacz [Jak skonfigurować funkcje izolacji sieci](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) w dokumentacji dewelopera Sklepu Windows 8.x.
  
## <a name="see-also"></a>Zobacz też

- [Łączenie się z usługą sieci web](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Wskazówki i lista kontrolna izolacji sieci](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Szybki start: łączenie się przy użyciu funkcji HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Jak korzystać z programów obsługi HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Jak zabezpieczyć połączenia HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Przykład httpclient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
