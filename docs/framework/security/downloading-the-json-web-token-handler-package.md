---
title: Pobieranie pakietu programu obsługi tokenów sieci Web JSON
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633525"
---
# <a name="download-the-json-web-token-handler-package"></a>Pobieranie pakietu programu obsługi tokenów Web JSON

W tym temacie omówiono sposób pobierania i używania programu obsługi tokenów Web JSON w projekcie.

Rozszerzenie JSON Web Token Handler jest dostępne jako pakiet NuGet, który dodaje niezbędne zespoły i odwołania do projektu. Jeśli nie masz jeszcze zainstalowanego Menedżera NuGet, przejdź do strony [nuget.org](https://nuget.org) go zainstalować. Można wyświetlić historię wersji rozszerzenia odwiedzając jego stronę na NuGet: [JSON Web Token Handler dla narzędzia NuGet](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)

## <a name="use-the-package-manager-gui"></a>Użyj Menedżera pakietów GUI

1. W programie Visual Studio, kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**.

2. W **Zarządzaj pakietami NuGet** okna, kliknij pole wyszukiwania i wprowadź `JWT Token Handler` i naciśnij klawisz **Enter**.

3. W okienku wyników kliknij **zainstalować** przycisku dla pierwszego wyniku.

4. Pakiet rozpocznie się pobieranie. Zanim zostanie dodany do projektu, pojawi się okno dialogowe akceptacja licencji. Jeśli akceptujesz postanowienia licencyjne, kliknij przycisk **akceptuję**.

5. Najnowsze zestawy programu obsługi tokenów Web JSON zostaną pobrane i dodane do projektu.

## <a name="use-the-package-manager-console"></a>Za pomocą konsoli Menedżera pakietów

1. W programie Visual Studio, kliknij przycisk **narzędzia** > **Menedżera pakietów NuGet** > **Konsola Menedżera pakietów**.

2. **Konsola Menedżera pakietów** pojawia się. Wprowadź poniższy tekst i naciśnij klawisz **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. Najnowsze zestawy programu obsługi tokenów Web JSON zostaną pobrane i dodane do projektu.
