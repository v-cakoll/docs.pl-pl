---
title: "Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bf6869de939ed7eda7cd3de868e712126f71751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy
W tym temacie omówiono sposób pobranie i użycie rejestru nazwy wystawcy sprawdzania poprawności (VINR) w projekcie.  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>Pobieranie sprawdzania poprawności rejestru nazwy dostawcy  
 VINR jest dostępna jako pakietu NuGet, który dodaje konieczne zestawy, a odwołania do projektu. Jeśli nie masz już zainstalowany NuGet, przejdź do [nuget.org](http://nuget.org) go zainstalować. Widać Historia wersji rozszerzenia odwiedzając jej stronę na NuGet: [rejestru sprawdzania poprawności nazwy wystawcy firmy Microsoft na NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>Pobieranie sprawdzanie poprawności rejestru nazwy dostawcy przy użyciu graficznego interfejsu użytkownika Menedżera pakietów  
  
1.  W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz **Zarządzaj pakietami NuGet**.  
  
2.  W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `ValidatingIssuerNameRegistry` i naciśnij klawisz **Enter**.  
  
3.  W okienku wyników kliknij **zainstalować** przycisku do pierwszego wyniku.  
  
4.  Pakiet zostanie rozpocząć pobieranie. Przed dodaniem jej do projektu, pojawi się okno dialogowe akceptacji licencji. Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.  
  
5.  Najnowsze zestawy VINR zostanie pobrany i dodane do projektu.  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>Pobieranie sprawdzanie poprawności rejestru nazwy dostawcy przy użyciu konsoli Menedżera pakietów  
  
1.  W programie Visual Studio, kliknij przycisk **narzędzia**, **Menedżer pakietów biblioteki**, a następnie **Konsola Menedżera pakietów**.  
  
2.  **Konsola Menedżera pakietów** pojawi się. Wprowadź poniższy tekst i naciśnij klawisz **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  Najnowsze zestawy VINR zostanie pobrany i dodane do projektu.
