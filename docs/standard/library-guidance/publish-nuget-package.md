---
title: Publikowanie pakietu NuGet
description: Zalecenia dotyczące najlepszych rozwiązań do publikowania NuGet biblioteki .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 036aa99c89790274628c40824be7e230d81850fe
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144072"
---
# <a name="publishing-a-nuget-package"></a>Publikowanie pakietu NuGet

Pakiety NuGet są publikowane i używane z repozytoriów pakietów. NuGet.org najczęściej jest znany i używane repozytorium, istnieje wiele miejsc, aby opublikować pakiety NuGet:

* **[NuGet.org](https://www.nuget.org/)**  głównej repozytorium online dla pakietów NuGet. Wszystkie pakiety w witrynie NuGet.org są publicznie dostępne dla wszystkich użytkowników. Domyślnie program Visual Studio zawiera NuGet.org jako źródło pakietów i wielu deweloperów NuGet.org znajduje się tylko repozytorium pakietów, który będzie interakcji z. NuGet.org to najlepsze miejsce do publikowania stabilne pakiety i pakiety w wersji wstępnej, które ma być opinii społeczności.

* **[MyGet](https://myget.org/)**  to usługa repozytorium, która obsługuje źródła danych pakiet niestandardowy w przypadku projektów typu open source. MyGet publiczne źródło niestandardowe to idealne miejsce do publikowania utworzone przez usługę CI pakiety w wersji wstępnej. MyGet także kanały prywatne dostępnym w sprzedaży.

* A **[lokalne źródła danych](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderem, takich jak repozytorium pakietów i sprawia, że `*.nupkg` pliki w folderze dostępne przez NuGet. Lokalne źródło danych jest przydatna przy testowaniu pakietu NuGet przed jego opublikowaniem NuGet.org.

> [!NOTE]
> NuGet.org [nie zezwala na pakiet do usunięcia](/nuget/policies/deleting-packages) po jego przekazaniu. Pakiet może być nieznajdujące się na liście, tak aby nie była widoczna publicznie w interfejsie użytkownika, ale `*.nupkg` nadal można pobrać podczas przywracania. Ponadto nuget.org nie zezwala na wersje zduplikowanych pakietów. Aby poprawić pakietu NuGet z powodu błędu konieczne wyrejestrowanie pakietu niepoprawne, zwiększ numer wersji, a następnie opublikować nową wersję pakietu.

**CZY ✔️** [publikowania stabilne pakiety i pakiety w wersji wstępnej](/nuget/create-packages/publish-a-package) chcesz, aby opinia społeczności do NuGet.org.

**ROZWAŻ ✔️** publikowania pakiety w wersji wstępnej MyGet źródła danych z kompilacji ciągłej integracji.

**ROZWAŻ ✔️** testowania w środowisku deweloperskim za pomocą lokalnego źródła danych lub MyGet. Sprawdź działa pakiet, a następnie opublikuj go w witrynie NuGet.org.

## <a name="nugetorg-security"></a>Zabezpieczenia NuGet.org

Jest ważne, nieupoważnione osoby nie można uzyskać dostępu do konta NuGet i przekazać złośliwego wersję biblioteki. NuGet.org oferuje two-Factor Authentication uwierzytelnianie i powiadomień e-mail po opublikowaniu pakietu. Włączyć te funkcje po zalogowaniu w witrynie NuGet.org **ustawienia konta** strony.

![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "zabezpieczenia konta NuGet")

**CZY ✔️** Użyj konta Microsoft do logowania się na NuGet.

**CZY ✔️** Włączanie uwierzytelniania dwuskładnikowego do uzyskiwania dostępu do NuGet.

**CZY ✔️** Włączanie powiadomień e-mail po opublikowaniu pakietu.

>[!div class="step-by-step"]
>[Poprzednie](sourcelink.md)
>[dalej](versioning.md)