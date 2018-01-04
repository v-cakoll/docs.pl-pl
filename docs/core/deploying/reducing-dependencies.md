---
title: "Zmniejszenie zależności pakietu z pliku project.json"
description: "Zmniejszenie zależności pakietu, podczas tworzenia biblioteki na podstawie pliku project.json."
keywords: .NET, .NET core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 916251e3-87f9-4eee-81ec-94076215e6fa
ms.workload: dotnetcore
ms.openlocfilehash: 858fc77d9652bfa59ed0bb3159260f40c76156a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="reducing-package-dependencies-with-projectjson"></a>Zmniejszenie zależności pakietu z pliku project.json

W tym artykule opisano, co należy wiedzieć o zmniejszeniu zależności pakietu, podczas tworzenia `project.json` biblioteki. Na koniec tego artykułu dowiesz się, jak utworzenie biblioteki w taki sposób, że używa tylko zależności, które są niezbędne. 

## <a name="why-its-important"></a>Dlaczego jest ważne

Oprogramowanie .NET core to produkt składają się z pakietami NuGet.  Pakiet niezbędne jest [. NETStandard.Library metapackage](https://www.nuget.org/packages/NETStandard.Library), która pakietu NuGet składa się z innymi pakietami.  Umożliwia zestaw pakietów, które mogą działać na wiele implementacji .NET, takich jak .NET Framework, .NET Core i Xamarin/Mono.

Jednakże istnieje szansa, że biblioteki nie będą korzystać co jeden pakiet, który zawiera.  Podczas tworzenia biblioteki i jej dystrybucji za pośrednictwem NuGet, jest najlepszym rozwiązaniem "Przycinanie" zależności dół tylko pakiety rzeczywiście używane.  Powoduje mniejsze zużycie ogólną pakietów NuGet.

## <a name="how-to-do-it"></a>Jak to zrobić

Obecnie nie są nie oficjalne `dotnet` polecenia, które usuwa odwołania do pakietu.  Zamiast tego należy to zrobić ręcznie.  Ogólny proces wygląda następująco:

1. Odwołanie `NETStandard.Library` wersji `1.6.0` w `dependencies` części Twojego `project.json`.
2. Przywracanie pakietów z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) z wiersza polecenia.
3. Sprawdź `project.lock.json` plików i Znajdź `NETSTandard.Library` sekcji.  Jest na początku pliku.
4. Skopiuj wszystkie pakiety wymienione w obszarze `dependencies`.
5. Usuń `.NETStandard.Library` odwołania i zastąp go skopiowanych pakietów.
6. Usuń odwołania do pakietów, które nie są potrzebne.


Można znaleźć pakiety, których nie ma potrzeby przez jeden z następujących sposobów:

1. Prób i błędów.  Obejmuje to usunięcie pakietu, przywracanie wyświetlany, jeśli biblioteka nadal kompiluje i powtórzyć ten proces.
2. Przy użyciu narzędzia, takie jak [ILSpy](http://ilspy.net) lub [reflektora .NET](http://www.red-gate.com/products/dotnet-development/reflector) wglądu odwołania, aby zobaczyć, co kod jest rzeczywiście przy użyciu.  Następnie można usunąć pakietów, które nie odnoszą się do typów, którego używasz.

## <a name="example"></a>Przykład 

Załóżmy, że zapisano bibliotekę, która podano dodatkowe funkcje typy kolekcji ogólnych.  Takie biblioteki musi być zależne od pakietów, takie jak `System.Collections`, ale może być w ogóle zależne od pakietów takich jak `System.Net.Http`.  Tak byłoby dobrej przyciąć zależności pakietu do co ta biblioteka wymagane tylko!

Aby przyciąć tej biblioteki, należy uruchomić z `project.json` i Dodaj odwołanie do `NETStandard.Library` wersji `1.6.0`.

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

Następnie należy przywrócić pakiety z `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), sprawdzić `project.lock.json` plików i Znajdź wszystkie pakiety przywrócone dla `NETSTandard.Library`.

Oto jakie odpowiedniej sekcji `project.lock.json` pliku wygląda podobnie, jeśli celem `netstandard1.0`:

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

Następnie skopiuj za pośrednictwem odwołania do pakietu do `dependencies` części biblioteki `project.json` pliku, zastępując `NETStandard.Library` odwołania:

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

Bardzo dużo pakietów, duża liczba które które na pewno nie są niezbędne do rozszerzania typy kolekcji.  Można ręcznie usunąć pakietów lub za pomocą narzędzia, takie jak [ILSpy](http://ilspy.net) lub [reflektora .NET](http://www.red-gate.com/products/dotnet-development/reflector) do identyfikowania, która faktycznie pakiety kodu używa.

Oto, jak może wyglądać przycięte pakietu:

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

Teraz, ma mniejszy wyświetlacz niż jeśli ma ono zależy na `NETStandard.Library` metapackage.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]