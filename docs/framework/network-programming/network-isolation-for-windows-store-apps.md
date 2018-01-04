---
title: Izolacja sieci dla aplikacji ze Sklepu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ba7e480f50d3a339648229f17152eb28b28ec159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolacja sieci dla aplikacji ze Sklepu Windows
Klasy w <xref:System.Net>, <xref:System.Net.Http>, i <xref:System.Net.Http.Headers> przestrzeni nazw może służyć do tworzenia aplikacji ze Sklepu Windows lub aplikacji klasycznych. Gdy są używane w aplikacji ze Sklepu Windows, klas w tych obszarach nazw dotyczy izolacji sieci, część używany przez model zabezpieczeń aplikacji [!INCLUDE[win8](../../../includes/win8-md.md)]. Możliwości odpowiedniej sieci musi być włączony w manifeście aplikacji dla aplikacji ze Sklepu Windows dla systemu w celu umożliwienia dostępu do sieci.  
  
## <a name="checklist-for-network-isolation"></a>Lista kontrolna dotycząca izolacji sieci  
 Użyj tej listy kontrolnej, należy upewnić się, że izolacja sieci jest skonfigurowany dla aplikacji ze Sklepu Windows.  
  
1.  Określ kierunek wymagane przez aplikację żądań dostępu do sieci. Może to być żądań wychodzących inicjowanej przez klienta lub niechciane żądania przychodzące lub może być kombinację obu typów sieci żądania.  
  
2.  Określ typ tej aplikacji będą komunikować się z zasobów sieciowych. Aplikacja może być konieczne do komunikowania się z zaufanych zasobów w sieci w domu lub pracy. Aplikacja może być konieczne do komunikowania się z zasobami przez Internet. Aplikacja może potrzebować dostępu do obu typów zasobów sieciowych.  
  
3.  Minimalna wymagana możliwości izolacji sieci należy skonfigurować w manifeście aplikacji.  
  
4.  Wdrażanie i uruchamianie aplikacji w taki sposób, aby przetestować go przy użyciu narzędzia izolacji sieci, które są dostępne w celu rozwiązywania problemów.  
  
 Aby uzyskać bardziej szczegółowe informacje na temat konfigurowania funkcji sieciowych i izolacja narzędzi używanych do rozwiązywania problemów w przypadku izolacji sieci, zobacz [sposobu konfigurowania możliwości izolacji sieci](http://go.microsoft.com/fwlink/?LinkID=228265) w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer dokumentacja.  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie z usługą sieci web](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [Wskazówki i Lista kontrolna dotycząca izolacji sieci](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [Szybki Start: Łączenie za pomocą elementu HttpClient](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [Jak używać HttpClient obsługi](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [Jak zabezpieczyć połączenia HttpClient](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [Przykładowe HttpClient](http://go.microsoft.com/fwlink/?LinkId=242550)
