---
title: Pobieranie pakietu sprawdzania poprawności rejestru nazwy dostawcy
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 833a0722fdd27df4e488ed7fac99444c6d9b8905
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316195"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>Pobieranie pakietu sprawdzania poprawności rejestru nazwy wystawcy

W tym temacie omówiono sposób pobierania i wykorzystywania rejestru nazwy wystawcy sprawdzania poprawności (VINR) w projekcie.

Rozszerzenie VINR jest dostępne jako pakiet NuGet, który dodaje niezbędne zespoły i odwołania do projektu. Jeśli nie masz jeszcze zainstalowanego Menedżera NuGet, przejdź do strony [nuget.org](https://nuget.org) go zainstalować. Można zobaczyć historię wersji rozszerzenia odwiedzając jego stronę na NuGet: [Microsoft Validating Issuer Name Registry dla narzędzia NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>Użyj Menedżera pakietów GUI

1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**.

2. W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `ValidatingIssuerNameRegistry` i naciśnij klawisz **Enter**.

3. W okienku wyników kliknij **zainstalować** przycisku dla pierwszego wyniku.

4. Pakiet rozpocznie się pobieranie. Zanim zostanie dodany do projektu, pojawi się okno dialogowe akceptacja licencji. Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.

5. Najnowsze zestawy VINR zostaną pobrane i dodane do projektu.

## <a name="use-the-package-manager-console"></a>Za pomocą konsoli Menedżera pakietów

1. W programie Visual Studio, kliknij przycisk **narzędzia** > **Menedżera pakietów NuGet** > **Konsola Menedżera pakietów**.

2. **Konsola Menedżera pakietów** pojawia się. Wprowadź poniższy tekst i naciśnij klawisz **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. Najnowsze zestawy VINR zostaną pobrane i dodane do projektu.