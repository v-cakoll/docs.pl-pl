---
title: Zmniejszanie zależności pakietu przy użyciu pliku Project. JSON
description: Zmniejszenie zależności pakietu podczas tworzenia bibliotek opartych na pliku Project. JSON.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740829"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Zmniejszanie zależności pakietu przy użyciu pliku Project. JSON

W tym artykule opisano, co należy wiedzieć o zmniejszeniu zależności pakietu podczas tworzenia bibliotek `project.json`. Na końcu tego artykułu dowiesz się, jak utworzyć bibliotekę w taki sposób, aby korzystała tylko z potrzeb.

## <a name="why-its-important"></a>Dlaczego jest ważne

.NET Core to produkt składający się z pakietów NuGet.  Istotnym pakietem jest [. Pakiet servicepackage. Library](https://www.nuget.org/packages/NETStandard.Library), który jest pakietem NuGet składającym się z innych pakietów. Zawiera zestaw pakietów, które są gwarantowane do pracy w wielu implementacjach platformy .NET, takich jak .NET Framework, .NET Core i Xamarin/mono.

Istnieje jednak dobry szansa, że biblioteka nie będzie używać każdego z nich.  W przypadku tworzenia biblioteki i dystrybucji jej za pośrednictwem programu NuGet najlepszym rozwiązaniem jest "przycinanie" zależności do tylko pakietów, których faktycznie używasz.  Powoduje to mniejsze ogólne rozmiary pakietów NuGet.

## <a name="how-to-do-it"></a>Jak to zrobić

Obecnie nie istnieje oficjalne polecenie `dotnet`, które przycina odwołania do pakietów.  Zamiast tego należy to zrobić ręcznie.  Ogólny proces wygląda następująco:

1. Informacje o wersji `NETStandard.Library` `1.6.0` w sekcji `dependencies` `project.json`.
2. Przywróć pakiety z `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia.
3. Sprawdź plik `project.lock.json` i Znajdź sekcję `NETStandard.Library`.  Znajduje się blisko początku pliku.
4. Skopiuj wszystkie pakiety z listy w obszarze `dependencies`.
5. Usuń odwołanie `.NETStandard.Library` i zastąp je skopiowanymi pakietami.
6. Usuń odwołania do pakietów, które nie są potrzebne.

Możesz dowiedzieć się, które pakiety nie są potrzebne, wykonując jedną z następujących czynności:

1. Wersja próbna i błąd. Obejmuje to usuwanie pakietu, przywracanie, wyświetlanie, czy biblioteka jest nadal skompilowana, i powtarzanie tego procesu.
2. Za pomocą narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector) , można uzyskać wgląd w odwołania, aby zobaczyć, do czego służy Twój kod. Następnie można usunąć pakiety, które nie odpowiadają typom, z którego korzystasz.

## <a name="example"></a>Przykład

Załóżmy, że Zapisano bibliotekę, która udostępnia dodatkowe funkcje dla typów kolekcji rodzajowych. Taka Biblioteka musi zależeć od pakietów, takich jak `System.Collections`, ale może nie zależeć od pakietów, takich jak `System.Net.Http`. W związku z tym dobrym sposobem jest przycinanie zależności pakietów do tylko potrzeb tej biblioteki.

Aby przyciąć tę bibliotekę, Zacznij od pliku `project.json` i Dodaj odwołanie do `NETStandard.Library` wersji `1.6.0`.

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

Następnie Przywróć pakiety z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), sprawdź plik `project.lock.json` i Znajdź wszystkie pakiety przywrócone dla `NETStandard.Library`.

Poniżej przedstawiono informacje o tym, co znajduje się w odpowiedniej sekcji w pliku `project.lock.json` podczas określania celu `netstandard1.0`:

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

Następnie skopiuj odwołania do pakietu do sekcji `dependencies` pliku `project.json` biblioteki, zastępując `NETStandard.Library` odwołanie:

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

Jest to dość wiele pakietów, z których wiele nie jest koniecznych do rozszerzania typów kolekcji.  Pakiety można usuwać ręcznie lub za pomocą narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [reflektor .NET](https://www.red-gate.com/products/dotnet-development/reflector/) , aby identyfikować, które pakiety rzeczywiście są używane w kodzie.

Oto, jak może wyglądać przycięty pakiet:

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

Teraz ma mniejsze rozmiary niż w przypadku, gdy zależą od pakietu `NETStandard.Library`.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
