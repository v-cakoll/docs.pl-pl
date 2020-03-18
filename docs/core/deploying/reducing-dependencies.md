---
title: Zmniejszanie zależności pakietów za pomocą projektu.json
description: Zmniejsz zależności pakietów podczas tworzenia bibliotek opartych na programie project.json.
author: cartermp
ms.date: 06/20/2016
ms.openlocfilehash: 48ba3ef578388fd98fe7cb830df313512d359483
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740829"
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Zmniejszanie zależności pakietów za pomocą projektu.json

W tym artykule omówiono, co należy wiedzieć o `project.json` zmniejszaniu zależności pakietu podczas tworzenia bibliotek. Na końcu tego artykułu dowiesz się, jak skomponować biblioteki w taki sposób, że używa tylko zależności, których potrzebuje.

## <a name="why-its-important"></a>Dlaczego jest to ważne

.NET Core to produkt złożony z pakietów NuGet.  Podstawowym pakietem jest [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), który jest pakietem NuGet składającym się z innych pakietów. Zapewnia zestaw pakietów, które są gwarantowane do pracy na wiele implementacji .NET, takich jak .NET Framework, .NET Core i Xamarin/Mono.

Istnieje jednak duża szansa, że biblioteka nie będzie używać każdego pakietu, który zawiera.  Podczas tworzenia biblioteki i dystrybucji go za pomocą NuGet, jest najlepszym rozwiązaniem do "przyciąć" zależności w dół tylko pakiety, które faktycznie używasz.  Powoduje to mniejszy ogólny rozmiar dla pakietów NuGet.

## <a name="how-to-do-it"></a>Jak to zrobić

Obecnie nie ma `dotnet` oficjalnego polecenia, które przycina odwołania do pakietu.  Zamiast tego musisz to zrobić ręcznie.  Ogólny proces wygląda następująco:

1. Wersja `NETStandard.Library` `1.6.0` referencyjna `dependencies` w `project.json`sekcji pliku .
2. Przywracanie `dotnet restore` pakietów z[(patrz uwaga)](#dotnet-restore-note)z wiersza polecenia.
3. Sprawdź `project.lock.json` plik i `NETStandard.Library` znajdź sekcję.  Znajduje się na początku pliku.
4. Skopiuj wszystkie `dependencies`wymienione pakiety w obszarze .
5. Usuń `.NETStandard.Library` odwołanie i zastąp je skopiowanymi pakietami.
6. Usuń odwołania do pakietów, których nie potrzebujesz.

Możesz dowiedzieć się, których pakietów nie potrzebujesz, jednym z następujących sposobów:

1. Próby i błędy. Wiąże się to usunięcie pakietu, przywrócenie, sprawdzanie, czy biblioteka nadal kompiluje i powtarzanie tego procesu.
2. Za pomocą narzędzia, takich jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [.NET Reflektor,](https://www.red-gate.com/products/dotnet-development/reflector) aby zerknąć na odwołania, aby zobaczyć, co kod jest faktycznie przy użyciu. Następnie można usunąć pakiety, które nie odpowiadają typom, których używasz.

## <a name="example"></a>Przykład

Wyobraź sobie, że napisałeś bibliotekę, która dostarczyła dodatkowe funkcje dla typów kolekcji ogólnych. Taka biblioteka musiałaby zależeć od `System.Collections`pakietów takich jak , ale `System.Net.Http`może wcale nie zależeć od pakietów takich jak . W związku z tym dobrze byłoby przyciąć zależności pakietów do tego, czego wymaga ta biblioteka!

Aby przyciąć tę bibliotekę, należy rozpocząć od `project.json` pliku i dodać odwołanie do `NETStandard.Library` wersji `1.6.0`.

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

Następnie przywracasz `dotnet restore` pakiety za pomocą `project.lock.json` [(patrz uwaga),](#dotnet-restore-note)sprawdź plik `NETStandard.Library`i znajdź wszystkie pakiety przywrócone dla .

Oto jak wygląda odpowiednia `project.lock.json` sekcja w `netstandard1.0`pliku podczas kierowania:

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

Następnie skopiuj odniesienia `dependencies` do pakietu do `project.json` sekcji pliku `NETStandard.Library` biblioteki, zastępując odwołanie:

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

To dość dużo pakietów, z których wiele z pewnością nie jest niezbędnych do rozszerzenia typów kolekcji.  Pakiety można usunąć ręcznie lub użyć narzędzia, takiego jak [ILSpy](https://github.com/icsharpcode/ILSpy#ilspy-------) lub [.NET Reflector,](https://www.red-gate.com/products/dotnet-development/reflector/) aby określić, które pakiety faktycznie używa kodu.

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

Teraz ma mniejszy ślad niż gdyby zależał od `NETStandard.Library` metapakietu.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
