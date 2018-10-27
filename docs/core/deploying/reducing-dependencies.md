---
title: Zmniejszenie zależności pakietów przy użyciu pliku project.json
description: Ogranicz zależności pakietów, podczas tworzenia bibliotek opartych na pliku project.json.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: 6da7404415e8d485533fc1c9a619cb0706a26aca
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2018
ms.locfileid: "50040884"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Zmniejszenie zależności pakietów przy użyciu pliku project.json

W tym artykule opisano, co musisz wiedzieć o zmniejszenie zależności pakietu, podczas tworzenia `project.json` bibliotek. Przy końcu tego artykułu dowiesz się, jak tworzyć biblioteki w taki sposób, że używa tylko zależności, których potrzebuje. 

## <a name="why-its-important"></a>Dlaczego jest ważne

.NET core jest produktem składają się z pakietów NuGet.  Pakiet niezbędne jest [. Meta Microsoft.aspnetcore.all NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library), ponieważ pakiet NuGet składa się z innymi pakietami.  Udostępnia zestaw pakietów, które mogą działać na wiele implementacji .NET, takich jak .NET Framework i .NET Core i Xamarin/Mono.

Jednakże istnieje szansa, że Twoja biblioteka nie będzie używać każdego pojedynczego pakietu, zawartych w nim.  Podczas tworzenia biblioteki i ich dystrybucję za pośrednictwem NuGet, jest najlepszym rozwiązaniem "Przycinanie" zależności do tylko pakiety rzeczywiście używane.  Skutkuje to mniejszą całkowitego rozmiaru pakietów NuGet.

## <a name="how-to-do-it"></a>Jak to zrobić

Obecnie nie ma żadnych official będzie przydatna `dotnet` polecenie, które usuwa odwołania do pakietu.  Zamiast tego musisz to zrobić ręcznie.  Ogólny proces wygląda podobnie do poniższego:

1. Odwołanie `NETStandard.Library` wersji `1.6.0` w `dependencies` części Twojej `project.json`.
2. Przywróć pakiety za pomocą `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) z wiersza polecenia.
3. Sprawdzanie `project.lock.json` plików i Znajdź `NETSTandard.Library` sekcji.  Jest na początku pliku.
4. Skopiuj wszystkie pakiety wymienione w obszarze `dependencies`.
5. Usuń `.NETStandard.Library` odwołania i zastąp go skopiowane pakiety.
6. Usuń odwołania do pakietów, które nie są potrzebne.


Możesz dowiedzieć się które pakiety, nie musisz za pomocą jednej z następujących sposobów:

1. Prób i błędów.  Obejmuje to usunięcie pakietu, przywracanie, wyświetlanie, jeśli Twoja Biblioteka nadal będzie się kompilować i powtórzyć ten proces.
2. Za pomocą narzędzia, takie jak [użyciu narzędzia do dekompilacji](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [odblaskowego .NET](https://www.red-gate.com/products/dotnet-development/reflector) wglądu odwołania, aby zobaczyć, co Twój kod faktycznie używa.  Następnie można usunąć pakiety, które nie odnoszą się do typów, których używasz.

## <a name="example"></a>Przykład 

Wyobraź sobie, autorem biblioteki, które podano dodatkowe funkcje do typów ogólnych kolekcji.  Takie biblioteki konieczne są zależne od pakietów, takich jak `System.Collections`, ale może być w ogóle nie zależy od pakietów takich jak `System.Net.Http`.  W efekcie byłoby dobrze trim zależności pakietów w dół, co ta biblioteka wymagane tylko!

Można przycięcia tej biblioteki, możesz zaczynać `project.json` pliku i Dodaj odwołanie do `NETStandard.Library` wersji `1.6.0`.

```json
{
    "version":"1.0.0",
    "dependencies":{
        "NETStandard.Library":"1.6.0"
    },
    "frameworks": {
        "netstandard1.0": {}
     }
}
```

Następnie przywróć pakiety za pomocą `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), sprawdź `project.lock.json` plików i Znajdź wszystkie pakiety, które są przywracane dla `NETSTandard.Library`.

Oto jakie odpowiedniej sekcji w `project.lock.json` pliku wygląda podobnie, gdy `netstandard1.0`:

```json
"NETStandard.Library/1.6.0":{
    "type": "package",
    "dependencies": {
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    }
}
```

Następnie skopiuj odwołania do pakietu do `dependencies` części biblioteki `project.json` pliku, zastępując `NETStandard.Library` odwołania:

```json
{
    "version":"1.0.0",
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Diagnostics.Debug": "4.0.11",
        "System.Diagnostics.Tools": "4.0.1",
        "System.Globalization": "4.0.11",
        "System.IO": "4.1.0",
        "System.Linq": "4.1.0",
        "System.Net.Primitives": "4.0.11",
        "System.ObjectModel": "4.0.12",
        "System.Reflection": "4.1.0",
        "System.Reflection.Extensions": "4.0.1",
        "System.Reflection.Primitives": "4.0.1",
        "System.Resources.ResourceManager": "4.0.1",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Text.Encoding": "4.0.11",
        "System.Text.Encoding.Extensions": "4.0.11",
        "System.Text.RegularExpressions": "4.1.0",
        "System.Threading": "4.0.11",
        "System.Threading.Tasks": "4.0.11",
        "System.Xml.ReaderWriter": "4.0.11",
        "System.Xml.XDocument": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
    }
}
```

To bardzo wiele pakietów, wiele z nich na pewno nie są niezbędne do rozszerzania typy kolekcji.  Można ręcznie usunąć pakiety lub użyj narzędzia takiego jak [użyciu narzędzia do dekompilacji](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [odblaskowego .NET](https://www.red-gate.com/products/dotnet-development/reflector/) do identyfikowania, która faktycznie pakiety kodu używa.

Poniżej przedstawiono, jak może wyglądać przycięty pakietu:

```json
{
    "dependencies":{
        "Microsoft.NETCore.Platforms": "1.0.1",
        "Microsoft.NETCore.Runtime": "1.0.2",
        "System.Collections": "4.0.11",
        "System.Linq": "4.1.0",
        "System.Runtime": "4.1.0",
        "System.Runtime.Extensions": "4.1.0",
        "System.Runtime.Handles": "4.0.1",
        "System.Runtime.InteropServices": "4.1.0",
        "System.Runtime.InteropServices.RuntimeInformation": "4.0.0",
        "System.Threading.Tasks": "4.0.11"
    },
    "frameworks":{
        "netstandard1.0": {}
     }
}
```

Teraz ma mniejszy wyświetlacz niż jeśli było ono zależy na `NETStandard.Library` meta Microsoft.aspnetcore.all.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]