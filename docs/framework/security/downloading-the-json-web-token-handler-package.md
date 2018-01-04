---
title: "Pobieranie pakietu programu obsługi tokenów sieci Web JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5982830404d8d8780bf41153741928b68dc5c7d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-json-web-token-handler-package"></a>Pobieranie pakietu programu obsługi tokenów sieci Web JSON
W tym temacie omówiono sposób pobierania i używania programu obsługi tokenów sieci Web JSON w projekcie.  
  
## <a name="downloading-the-json-web-token-handler"></a>Pobieranie programu obsługi tokenów sieci Web JSON  
 Rozszerzenia JSON programu obsługi tokenów sieci Web jest dostępna jako pakietu NuGet, który dodaje konieczne zestawy, a odwołania do projektu. Jeśli nie masz już zainstalowany NuGet, przejdź do [nuget.org](http://nuget.org) go zainstalować. Widać Historia wersji rozszerzenia odwiedzając jej stronę na NuGet: [obsługi tokenów sieci Web JSON na NuGet](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a>Pobieranie programu obsługi tokenów sieci Web JSON przy użyciu graficznego interfejsu użytkownika Menedżera pakietów  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz **Zarządzaj pakietami NuGet**.  
  
2.  W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `JWT Token Handler` i naciśnij klawisz **Enter**.  
  
3.  W okienku wyników kliknij **zainstalować** przycisku do pierwszego wyniku.  
  
4.  Pakiet zostanie rozpocząć pobieranie. Przed dodaniem jej do projektu, pojawi się okno dialogowe akceptacji licencji. Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.  
  
5.  Najnowsze zestawów programu obsługi tokenów sieci Web JSON zostanie pobrany i dodane do projektu.  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a>Pobieranie programu obsługi tokenów sieci Web JSON przy użyciu konsoli Menedżera pakietów  
  
1.  W programie Visual Studio, kliknij przycisk **narzędzia**, **Menedżer pakietów biblioteki**, a następnie **Konsola Menedżera pakietów**.  
  
2.  **Konsola Menedżera pakietów** pojawi się. Wprowadź poniższy tekst i naciśnij klawisz **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  Najnowsze zestawów programu obsługi tokenów sieci Web JSON zostanie pobrany i dodane do projektu.
