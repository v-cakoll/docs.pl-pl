---
title: Izolacja sieci dla aplikacji ze sklepu Windows Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0d08b09f4ed0314d4f235f10b69bbf1343935841
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333265"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolacja sieci dla aplikacji ze sklepu Windows Store
Klasy w <xref:System.Net>, <xref:System.Net.Http>, i <xref:System.Net.Http.Headers> przestrzeni nazw może służyć do tworzenia aplikacji Windows Store lub aplikacjami pulpitu. W przypadku użycia w aplikacji Windows Store, klas w tych obszarach nazw dotyczy izolacji sieci, częścią modelu zabezpieczeń aplikacji, które są używane przez [!INCLUDE[win8](../../../includes/win8-md.md)]. Możliwości odpowiedniej sieci musi być włączony w manifeście aplikacji dla aplikacji Windows Store dla systemu zezwolić na dostęp do sieci.  
  
## <a name="checklist-for-network-isolation"></a>Lista kontrolna na potrzeby izolacji sieciowej  
 Użyj tej listy kontrolnej, należy upewnić się, że izolacja sieciowa jest skonfigurowany dla aplikacji Windows Store.  
  
1. Określ kierunek żądań dostępu do sieci wymagane przez aplikację. Może to być wychodzącego zainicjowane przez klienta żądania lub żądania przychodzące niechciane lub może być kombinację obu tych typów żądań sieci.  
  
2. Określanie typu aplikacji będą komunikować się z zasobów sieciowych. Aplikacja może być konieczne do komunikowania się z zaufanych zasobów w domu lub pracy sieci. Aplikacja może być konieczne do komunikowania się z zasobami przez Internet. Aplikacja może potrzebować dostępu do obu rodzajów zasobów sieciowych.  
  
3. Skonfiguruj minimalną wymaganą możliwości izolacji sieci w manifeście aplikacji.  
  
4. Wdrażanie i uruchamianie aplikacji, aby przetestować go za pomocą narzędzia izolacji sieci, które są dostarczane do rozwiązywania problemów.  
  
 Aby uzyskać bardziej szczegółowe informacje dotyczące sposobu konfigurowania funkcji sieciowych i izolacji narzędzi używanych do rozwiązywania problemów izolacji sieci, zobacz [sposobu konfigurowania możliwości izolacji sieci](https://go.microsoft.com/fwlink/?LinkID=228265) w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dla deweloperów dokumentacja.  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie z usługą sieci web](https://go.microsoft.com/fwlink/?LinkID=245696)
- [Wskazówki i listy kontrolne do izolacji sieci](https://go.microsoft.com/fwlink/?LinkID=228265)
- [Szybki start: Łączenie za pomocą elementu HttpClient](https://go.microsoft.com/fwlink/?LinkId=245697)
- [Jak używać klasy HttpClient obsługi](https://go.microsoft.com/fwlink/?LinkId=245699)
- [Jak zabezpieczyć HttpClient połączeń](https://go.microsoft.com/fwlink/?LinkId=245698)
- [Przykładowe klasy HttpClient](https://go.microsoft.com/fwlink/?LinkId=242550)
