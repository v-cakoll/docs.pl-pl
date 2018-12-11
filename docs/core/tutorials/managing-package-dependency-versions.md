---
title: Jak zarządzać wersjami zależności pakietu dla platformy .NET Core 1.0
description: Dowiedz się o zarządzanie wersjami zależności pakietu dla aplikacji i bibliotek platformy .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 7d7133ddb8717db1b830e531955454925c31a728
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168614"
---
# <a name="how-to-manage-package-dependency-versions-for-net-core-10"></a>Jak zarządzać wersjami zależności pakietu dla platformy .NET Core 1.0

W tym artykule opisano, co musisz wiedzieć o wersji pakietu dla aplikacji i bibliotek platformy .NET Core.

## <a name="glossary"></a>Słownik

**Napraw** — naprawianie zależności oznacza, że używasz tej samej "rodziny" pakietów wydanych dla narzędzia NuGet dla platformy .NET Core 1.0.

**Meta Microsoft.aspnetcore.all** — pakiet NuGet, który reprezentuje zestaw pakietów NuGet.

**Przycinanie** -oznacza usunięcie pakietów nie zależą od meta Microsoft.aspnetcore.all.  Jest to coś, co jest istotne dla autorów pakietu NuGet.  Zobacz [zmniejszenia zależności pakietów przy użyciu pliku project.json](../deploying/reducing-dependencies.md) Aby uzyskać więcej informacji. 

## <a name="fix-your-dependencies-to-net-core-10"></a>Naprawianie zależności do platformy .NET Core 1.0

Niezawodne przywrócenia pakietów i pisanie niezawodnego kodu, ważne jest rozwiązaniu zależności do wersji pakietów wysyłania wraz z platformy .NET Core 1.0.  Oznacza to, że każdego pakietu, powinien mieć tylko jedną jego wersję z nie dodatkowych kwalifikatorach.

**Przykłady pakietów stałą 1.0**

`"System.Collections":"4.0.11"`

`"NETStandard.Library":"1.6.0"`

`"Microsoft.NETCore.App":"1.0.0"`

**Przykładowe pakiety, które nie zostały usunięte ze 1.0**

`"Microsoft.NETCore.App":"1.0.0-rc4-00454-00"`

`"System.Net.Http":"4.1.0-*"`

`"System.Text.RegularExpressions":"4.0.10-rc3-24021-00"`

### <a name="why-does-this-matter"></a>Dlaczego jest to istotne?

Firma Microsoft gwarantuje, że jeśli możesz rozwiązać zależności do jakich dostarczany wraz z platformy .NET Core 1.0, te pakiety będą współpracują ze sobą. Nie ma takich gwarancji Jeśli korzystanie z pakietów, które nie są ustalone w ten sposób.

### <a name="scenarios"></a>Scenariusze

Mimo że znajduje się lista big wszystkie pakiety i ich wersji wydanej z platformy .NET Core 1.0, nie masz do wyszukiwania przez nią, jeśli Twój kod znajduje się w niektórych scenariuszach.

**Czy zależności tylko w systemach** `NETStandard.Library` **?**

Jeśli tak, którą powinieneś naprawić swoje `NETStandard.Library` pakietu do wersji `1.6`.  Ponieważ wyselekcjonowanych meta Microsoft.aspnetcore.all jego zamknięcia pakietu również zostanie usunięty z wersji 1.0.

**Czy zależności tylko w systemach** `Microsoft.NETCore.App` **?**

Jeśli tak, którą powinieneś naprawić swoje `Microsoft.NETCore.App` pakietu do wersji `1.0.0`.  Ponieważ wyselekcjonowanych meta Microsoft.aspnetcore.all jego zamknięcia pakietu również zostanie usunięty z wersji 1.0.

**Czy [przycinania](../deploying/reducing-dependencies.md) swoje** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **zależności meta Microsoft.aspnetcore.all?**

Jeśli tak, należy upewnić się, że meta Microsoft.aspnetcore.all, który jest uruchamiany, za pomocą zostanie usunięty z wersji 1.0.  Indywidualne pakiety, które są zależne od po przycięciu również są stałe do 1,0.

**Czy w zależności od pakietów poza** `NETStandard.Library` **lub** `Microsoft.NETCore.App` **metapakiety?**

Jeśli tak, należy naprawianie zależności do 1,0.  Zobacz wersje poprawny pakiet i numery na końcu tego artykułu.

### <a name="a-note-on-using-a-splat-string--when-versioning"></a>Uwaga dotycząca przy użyciu ciągu splat (\*) podczas przechowywania wersji

Przyjęła wzorzec przechowywania wersji, który używa splat (\*) ciąg następująco: `"System.Collections":"4.0.11-*"`.

**Nie należy tego robić**.  Przy użyciu ciągu splat może spowodować Trwa przywracanie pakietów z różnych kompilacji, z których część może być dalej w tym samym niż platformy .NET Core 1.0.  Następnie może to spowodować niektóre pakiety są niezgodne.

## <a name="packages-and-version-numbers-organized-by-metapackage"></a>Pakiety i numery wersji uporządkowane według meta Microsoft.aspnetcore.all

[Lista wszystkich pakietów .NET Standard i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/corefx/release/1.0.0/Latest_Packages.txt).

[Lista wszystkich pakietów środowiska uruchomieniowego i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/coreclr/release/1.0.0/LKG_Packages.txt).

[Lista wszystkich pakietów aplikacji .NET Core i ich wersji 1.0](https://github.com/dotnet/versions/blob/master/build-info/dotnet/core-setup/release/1.0.0/Latest_Packages.txt).
