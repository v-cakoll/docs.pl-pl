---
title: Publikowanie pakietu NuGet
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących publikowania bibliotek .NET w programie NuGet.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744552"
---
# <a name="publishing-a-nuget-package"></a>Publikowanie pakietu NuGet

Pakiety NuGet są publikowane i używane z repozytoriów pakietów. Chociaż NuGet.org jest najczęściej znanym i używanym repozytorium, istnieje wiele miejsc do publikowania pakietów NuGet:

* **[NuGet.org](https://www.nuget.org/)** to podstawowe repozytorium online dla pakietów NuGet. Wszystkie pakiety na NuGet.org są publicznie dostępne dla wszystkich użytkowników. Domyślnie program Visual Studio ma NuGet.org jako źródło pakietu, a dla wielu deweloperów NuGet.org jest jedynym repozytorium pakietu, z którym będą korzystać. NuGet.org to najlepsze miejsce do publikowania stabilnych pakietów i pakietów w wersji wstępnej, na które chcesz uzyskać opinię społecznościową.

* **[MyGet](https://myget.org/)** to usługa repozytorium, która obsługuje niestandardowe źródła pakietów dla projektów typu open source. Publiczne niestandardowe źródło danych MyGet jest idealnym miejscem do publikowania pakietów w wersji wstępnej utworzonych przez usługę CI. MyGet również udostępnia prywatne źródła komercyjne.

* **[Lokalne źródło danych](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderu, takiego jak repozytorium pakietu, i udostępnia `*.nupkg` pliki w folderze dostępnym dla narzędzia NuGet. Lokalne źródło danych jest przydatne w przypadku testowania pakietu NuGet przed opublikowaniem go w usłudze NuGet.org.

> [!NOTE]
> NuGet.org nie [zezwala na usunięcie pakietu](/nuget/policies/deleting-packages) po jego przekazaniu. Pakiet może być wystawiony, aby nie był publicznie widoczny w interfejsie użytkownika, ale `*.nupkg` nadal można pobrać podczas przywracania. Ponadto nuget.org nie zezwala na duplikowanie wersji pakietu. Aby poprawić pakiet NuGet z błędem należy usunąć listę niepoprawnego pakietu, zwiększyć numer wersji i opublikować nową wersję pakietu.

✔️ [publikować pakiety stabilne i pakiety wersji wstępnej](/nuget/create-packages/publish-a-package) , na które chcesz, aby opinia społeczności była NuGet.org.

✔️ ROZWAŻYĆ opublikowanie pakietów w wersji wstępnej do źródła danych MyGet z kompilacji ciągłej integracji.

✔️ ROZWAŻYĆ testowanie pakietów w środowisku programistycznym przy użyciu lokalnego źródła danych lub MyGet. Sprawdź, czy pakiet działa, a następnie opublikuj go w NuGet.org.

## <a name="nugetorg-security"></a>Zabezpieczenia NuGet.org

Ważne jest, aby niektórym uczestnikom nie mógł uzyskać dostępu do konta NuGet i przekazać złośliwą wersję biblioteki. NuGet.org oferuje uwierzytelnianie dwuskładnikowe i powiadomienia e-mail w przypadku opublikowania pakietu. Te funkcje należy włączyć po zalogowaniu się do NuGet.org na stronie **Ustawienia konta** .

![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "Zabezpieczenia konta NuGet")

✔️ używać konto Microsoft do logowania się do narzędzia NuGet.

✔️ włączyć uwierzytelnianie dwuskładnikowe w celu uzyskania dostępu do programu NuGet.

✔️ włączyć powiadomienia e-mail po opublikowaniu pakietu.

>[!div class="step-by-step"]
>[Poprzednie](sourcelink.md)
>[dalej](versioning.md)
