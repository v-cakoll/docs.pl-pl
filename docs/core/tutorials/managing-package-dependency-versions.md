---
title: "Jak zarządzać wersji zależności pakietu dla platformy .NET Core 1.0"
description: "Więcej informacji na temat zarządzania wersji zależności pakietu dla bibliotek .NET Core i aplikacji."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 4424a947-bdf9-4775-8d48-dc350a4e0aee
ms.workload: dotnetcore
ms.openlocfilehash: 2bb55f3bcd6678a127f099afbb9461cafe1a9c94
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>Jak zarządzać wersji zależności pakietu dla platformy .NET Core 1.0

W tym artykule opisano, co należy wiedzieć o wersji pakietu dla bibliotek .NET Core i aplikacji.

## <a name="glossary"></a>Słownik

**Usuń** -ustalania zależności oznacza, że używasz tego samego "rodziny" pakiety wydanej w dniu NuGet dla programu .NET Core 1.0.

**Metapackage** -pakietu A NuGet, który reprezentuje zestaw pakietów NuGet.

**Przycinanie** -oznacza usunięcie pakietów nie zależą od metapackage.  Jest to coś, które są odpowiednie dla autorów pakietu NuGet.  Zobacz [zmniejszenia zależności pakietu z pliku project.json](../deploying/reducing-dependencies.md) Aby uzyskać więcej informacji. 

## <a name="fix-your-dependencies-to-net-core-10"></a>Usuń zależności .NET Core 1.0

Aby niezawodnie przywracania pakietów i pisanie niezawodnego kodu, ważne jest, aby naprawieniu zależności do wersji pakietów wysyłania obok .NET Core 1.0.  Oznacza to, że każdy pakiet ma jedną wersję z nie dodatkowych kwalifikatorów.

**Przykłady pakietów stałą 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Przykładowe pakiety, które nie zostały usunięte 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Dlaczego ta sprawa?

Firma Microsoft gwarantuje, że jeśli rozwiązać zależności do jakiego jest dostarczany razem .NET Core 1.0, pakiety zostaną współpracują ze sobą. Jeśli używasz pakiety, które nie są ustalone w ten sposób jest żadnej gwarancji, takie.

### <a name="scenarios"></a>Scenariusze

Ma dużą listę wszystkich pakietów i ich wersje publikowana z .NET Core 1.0, ale nie masz do wyszukiwania przy jego użyciu, jeśli kod znajduje się w niektórych scenariuszach.

**Czy zależności tylko w systemie** `NETStandard.Library` **?**

Jeśli tak, należy naprawić Twojej `NETStandard.Library` pakietu do wersji `1.6`.  Ponieważ jest to wyselekcjonowanych metapackage, jego zamknięcia pakietu jest również stałą 1.0.

**Czy zależności tylko w systemie** `Microsoft.NETCore.App` **?**

Jeśli tak, należy naprawić Twojej `Microsoft.NETCore.App` pakietu do wersji `1.0.0`.  Ponieważ jest to wyselekcjonowanych metapackage, jego zamknięcia pakietu jest również stałą 1.0.

**Czy [przycinanie](../deploying/reducing-dependencies.md) Twojego** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapackage zależności?**

Jeśli tak, należy upewnić się, że metapackage, który jest uruchamiany z jest stałą 1.0.  Indywidualne pakiety, które są zależne od po przycięciu są również stałą 1.0.

**Czy w zależności od pakietów poza** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapackages?**

Jeśli tak, należy rozwiązać zależności do 1,0.  Zobacz wersje pakietów poprawne i numery na końcu tego artykułu kompilacji.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Uwaga na użycie ciągu splat (\*) podczas kontroli wersji

Przyjęte wzorzec przechowywania wersji, który używa splat (\*) ciąg następująco: `"System.Collections":"4.0.11-*"`.

**Nie należy tego robić**.  Przy użyciu parametrów splat może spowodować Przywracanie pakietów z różnych kompilacji, z których część może być dalej wzdłuż niż .NET Core 1.0.  Następnie może to spowodować niektóre pakiety są niezgodne.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Pakiety i uporządkowane według Metapackage numery wersji

[Lista wszystkich pakietów .NET Standard i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Lista wszystkich pakietów środowiska uruchomieniowego i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Lista wszystkich pakietów aplikacji .NET Core i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
