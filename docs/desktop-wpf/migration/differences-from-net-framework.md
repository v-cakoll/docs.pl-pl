---
title: Różnice między programem .NET Framework a programem .NET Core
description: W tym artykule opisano różnice między implementacją programu .NET Framework programu Windows Presentation Foundation (WPF) i .NET Core WPF. Podczas migracji aplikacji należy wziąć pod uwagę te niezgodności.
author: thraka
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 341e576f17c522fbcbb9c417176e9d4a13ab1b18
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82072208"
---
# <a name="differences-in-wpf"></a>Różnice w WPF

W tym artykule opisano różnice między programem Windows Presentation Foundation (WPF) w programie .NET Core i .NET Framework. WPF WPF dla .NET Core jest [platformą open source](https://github.com/dotnet/wpf) rozwidlił z oryginalnego WPF dla .NET Framework kod źródłowy.

Istnieje kilka funkcji programu .NET Framework, których program .NET Core nie obsługuje. Aby uzyskać więcej informacji na temat nieobsługiwałych technologii, zobacz [.NET Framework technologie niedostępne w programie .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projekty w stylu SDK

Program .NET Core używa plików projektu w stylu SDK. Te pliki projektu różnią się od tradycyjnych plików projektu .NET Framework zarządzanych przez program Visual Studio. Aby przeprowadzić migrację aplikacji .NET Framework WPF do platformy .NET Core, należy przekonwertować projekty. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji WPF do platformy .NET Core 3.0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Odwołania do pakietu NuGet

Jeśli aplikacja .NET Framework wyświetla jej zależności NuGet w pliku *packages.config,* należy przeprowadzić migrację do formatu: [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files)

1. W programie Visual Studio otwórz okienko **Eksploratora rozwiązań.**
1. W projekcie WPF kliknij prawym przyciskiem myszy **packages.config** > **Migrate packages.config to PackageReference**.

![Uaktualnianie do packageReference](media/differences-from-net-framework/package-reference-migration.png)

Pojawi się okno dialogowe pokazujące obliczone zależności NuGet najwyższego poziomu i pytanie, które inne pakiety NuGet powinny być promowane do najwyższego poziomu. Wybierz **przycisk OK,** a plik *packages.config* `<PackageReference>` zostanie usunięty z projektu, a elementy zostaną dodane do pliku projektu.

Gdy projekt używa, `<PackageReference>`pakiety nie są przechowywane lokalnie w folderze *Pakiety,* są przechowywane globalnie. Otwórz plik projektu i `<Analyzer>` usuń wszystkie elementy, które odnoszą się do folderu *Packages.* Analizatory te są automatycznie dołączone do odwołań do pakietu NuGet.

## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu

Zabezpieczenia dostępu do kodu (CAS) nie są obsługiwane przez program .NET Core ani WPF dla platformy .NET Core. Wszystkie funkcje związane z CAS są traktowane przy założeniu pełnego zaufania. WPF WPF dla platformy .NET Core usuwa kod związany z CAS. Publicznej powierzchni interfejsu API tych typów nadal istnieje, aby upewnić się, że wywołania do tych typów zakończyć się pomyślnie.

Publicznie zdefiniowane typy związane z CAS zostały przeniesione z zestawów WPF i do core .NET zestawy biblioteki. Zestawy WPF mają zestaw przekazywania tekstu do nowej lokalizacji przeniesionych typów.

| Zespół źródłowy | Zestaw docelowy | Typ                |
| --------------- | --------------- | ------------------- |
| *Windowsbase.dll* | *Plik System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *Plik System.Xaml.dll* | *Plik System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *Plik System.Xaml.dll* | *Plik System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Aby zminimalizować tarcie portów, funkcje przechowywania i pobierania informacji związanych z następującymi `XamlAccessLevel` właściwościami zostały zachowane w typie.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak przenieść aplikację .NET Framework WPF do platformy .NET Core.](convert-project-from-net-framework.md)
