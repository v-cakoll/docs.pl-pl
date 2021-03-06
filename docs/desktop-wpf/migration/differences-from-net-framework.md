---
title: Różnice między .NET Framework i .NET Core
description: Opisuje różnice między implementacją .NET Framework Windows Presentation Foundation (WPF) i .NET Core WPF. Podczas migrowania aplikacji należy wziąć pod uwagę te niezgodności.
author: adegeo
ms.date: 09/21/2019
ms.author: adegeo
ms.openlocfilehash: 3bedc30046c36d4c5430feedf5854276ebaef8aa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325691"
---
# <a name="differences-in-wpf"></a>Różnice w WPF

W tym artykule opisano różnice między Windows Presentation Foundation (WPF) na platformie .NET Core i .NET Framework. WPF for .NET Core to [Struktura "open source"](https://github.com/dotnet/wpf) powarta na podstawie oryginalnego programu WPF dla .NET Framework kodu źródłowego.

Istnieje kilka funkcji .NET Framework, które nie są obsługiwane przez platformę .NET Core. Aby uzyskać więcej informacji na temat nieobsługiwanych technologii, zobacz [technologie .NET Framework niedostępne w programie .NET Core](../../core/porting/net-framework-tech-unavailable.md).

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sdk-style-projects"></a>Projekty w stylu zestawu SDK

.NET Core używa plików projektu w stylu zestawu SDK. Te pliki projektu różnią się od tradycyjnych plików projektu .NET Framework zarządzanych przez program Visual Studio. Aby migrować .NET Framework aplikacje WPF do programu .NET Core, należy przekonwertować projekty. Aby uzyskać więcej informacji, zobacz [Migrowanie aplikacji WPF do programu .NET Core 3,0](convert-project-from-net-framework.md).

## <a name="nuget-package-references"></a>Odwołania do pakietu NuGet

Jeśli Twoja aplikacja .NET Framework wyświetli zależności NuGet w pliku *packages.config* , Przeprowadź migrację do [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) formatu:

1. W programie Visual Studio Otwórz okienko **Eksplorator rozwiązań** .
1. W projekcie WPF kliknij prawym przyciskiem myszy **packages.config**  >  **zmigrować packages.config do PackageReference**.

![Uaktualnianie do PackageReference](media/differences-from-net-framework/package-reference-migration.png)

Zostanie wyświetlone okno dialogowe przedstawiające obliczone zależności NuGet najwyższego poziomu i pytanie, które inne pakiety NuGet mają być podwyższenie poziomu. Wybierz **przycisk OK** , a plik *packages.config* zostanie usunięty z projektu, a `<PackageReference>` elementy zostaną dodane do pliku projektu.

Gdy Twój projekt `<PackageReference>` jest używany, pakiety nie są przechowywane lokalnie w folderze *Packages* , są przechowywane globalnie. Otwórz plik projektu i Usuń wszystkie `<Analyzer>` elementy, które odwołują się do folderu *Packages* . Te analizatory są automatycznie dołączane do odwołania do pakietu NuGet.

## <a name="code-access-security"></a>Zabezpieczenia dostępu kodu

Zabezpieczenia dostępu kodu (CAS) nie są obsługiwane przez platformę .NET Core lub WPF dla platformy .NET Core. Wszystkie funkcje związane z urzędem certyfikacji są traktowane w ramach założeń pełnego zaufania. Program WPF for .NET Core usuwa kod związany z urzędem certyfikacji. Publiczna powierzchnia interfejsu API tych typów nadal istnieje, aby upewnić się, że wywołania do tych typów powiodło się.

Publicznie zdefiniowane typy związane z urzędem certyfikacji zostały przeniesione z zestawów WPF i do zestawów podstawowych bibliotek platformy .NET. Zestawy WPF mają ustawioną funkcję przesyłania dalej typu na nową lokalizację przenoszonych typów.

| Zestaw źródłowy | Zestaw docelowy | Typ                |
| --------------- | --------------- | ------------------- |
| *WindowsBase.dll* | *System.Security.Permissions.dll* | <xref:System.Security.Permissions.MediaPermission> <br /> <xref:System.Security.Permissions.MediaPermissionAttribute> <br /> <xref:System.Security.Permissions.MediaPermissionAudio> <br /> <xref:System.Security.Permissions.MediaPermissionImage> <br /> <xref:System.Security.Permissions.MediaPermissionVideo> <br /> <xref:System.Security.Permissions.WebBrowserPermission> <br /> <xref:System.Security.Permissions.WebBrowserPermissionAttribute> <br /> <xref:System.Security.Permissions.WebBrowserPermissionLevel> |
| *System.Xaml.dll* | *System.Security.Permissions.dll* | <xref:System.Xaml.Permissions.XamlLoadPermission> |
| *System.Xaml.dll* | *System.Windows.Extension.dll*    | <xref:System.Xaml.Permissions.XamlAccessLevel><br/> |

> [!NOTE]
> Aby zminimalizować tarcie do przenoszenia, funkcje przechowywania i pobierania informacji związanych z poniższymi właściwościami zostały zachowane w `XamlAccessLevel` typie.
>
> - `PrivateAccessToTypeName`
> - `AssemblyNameString`

## <a name="next-steps"></a>Następne kroki

- [Dowiedz się, jak portować .NET Framework aplikację WPF do programu .NET Core.](convert-project-from-net-framework.md)
