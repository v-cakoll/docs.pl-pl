---
title: Publikowanie pakietu NuGet
description: Najlepsze zalecenia dotyczące publikowania bibliotek .NET w nuget.
ms.date: 10/02/2018
ms.openlocfilehash: 089c660bc51252c6295858b1462ae59bde968564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744552"
---
# <a name="publishing-a-nuget-package"></a>Publikowanie pakietu NuGet

Pakiety NuGet są publikowane i używane z repozytoriów pakietów. Chociaż NuGet.org jest najbardziej znanym i używanym repozytorium, istnieje wiele miejsc do publikowania pakietów NuGet:

* **[NuGet.org](https://www.nuget.org/)** jest podstawowym repozytorium online dla pakietów NuGet. Wszystkie pakiety na NuGet.org są publicznie dostępne dla wszystkich. Domyślnie program Visual Studio ma NuGet.org jako źródło pakietu, a dla wielu deweloperów NuGet.org jest jedynym repozytorium pakietów, z którymi będą współpracować. NuGet.org jest najlepszym miejscem do publikowania stabilnych pakietów i pakietów w wersji wstępnej, na których chcesz uzyskać opinię społeczności.

* **[MyGet](https://myget.org/)** to usługa repozytorium, która obsługuje niestandardowe źródła danych pakietów dla projektów typu open source. MyGet publicznego niestandardowego źródła danych jest idealnym miejscem do publikowania pakietów w wersji wstępnej utworzonych przez usługę ci. MyGet zapewnia również prywatne kanały handlowe.

* **[Lokalny kanał informacyjny](/nuget/hosting-packages/local-feeds)** umożliwia traktowanie folderu jak repozytorium `*.nupkg` pakietów i sprawia, że pliki w folderze są dostępne przez NuGet. Lokalny kanał informacyjny jest przydatny do testowania pakietu NuGet przed opublikowaniem go do NuGet.org.

> [!NOTE]
> NuGet.org [nie zezwala na usunięcie pakietu](/nuget/policies/deleting-packages) po jego przesłaniu. Pakiet może być niepubliczny, dzięki czemu nie jest publicznie widoczny `*.nupkg` w ui, ale nadal można go pobrać przy przywracaniu. Ponadto nuget.org nie zezwala na zduplikowane wersje pakietów. Aby poprawić pakiet NuGet z błędem, musisz odsunąć listę niepoprawnego pakietu, podwoż numer wersji i opublikować nową wersję pakietu.

✔️ [publikujstabilne pakiety i pakiety w wersji wstępnej,](/nuget/create-packages/publish-a-package) na których chcesz NuGet.org.

✔️ ROZWAŻ publikowanie pakietów w wersji wstępnej do kanału informacyjnego MyGet z kompilacji ciągłej integracji.

✔️ ROZWAŻ testowanie pakietów w środowisku programistycznym przy użyciu lokalnego źródła danych lub MyGet. Sprawdź, czy pakiet działa, a następnie opublikuj go w NuGet.org.

## <a name="nugetorg-security"></a>NuGet.org bezpieczeństwo

Ważne jest, aby złe podmioty nie mogły uzyskać dostępu do konta NuGet i przekazać złośliwą wersję biblioteki. NuGet.org oferuje uwierzytelnianie dwuskładnikowe i powiadomienia e-mail po opublikowaniu pakietu. Włącz te funkcje po zalogowaniu się do NuGet.org na stronie **Ustawienia konta.**

![tekst alternatywny](./media/publish-nuget-package/nuget-2fa.png "Zabezpieczenia konta NuGet")

✔️ do logowania się do NuGet za pomocą konta Microsoft.

✔️ do włączania uwierzytelniania dwuskładnikowego do uzyskiwania dostępu nuget.

✔️ włącz powiadomienia e-mail po opublikowaniu pakietu.

>[!div class="step-by-step"]
>[Poprzedni](sourcelink.md)
>[następny](versioning.md)
