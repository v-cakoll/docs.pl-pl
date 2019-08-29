---
title: Istotne zmiany i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań dotyczących nawigowania po zmianach podczas tworzenia bibliotek .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 6881b8737d9dd3fa7fa71f099fa1dc97b747033d
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104658"
---
# <a name="breaking-changes"></a>Fundamentalne zmiany

Ważne jest, aby w bibliotece .NET znaleźć równowagę między stabilnością dla istniejących użytkowników i innowacji w przyszłości. Autorzy biblioteki mają do refaktoryzacji i reprezentacji kodu do momentu idealnego, ale przerwanie istniejących użytkowników ma negatywny wpływ, szczególnie w przypadku bibliotek niskiego poziomu.

## <a name="project-types-and-breaking-changes"></a>Typy projektów i istotne zmiany

Sposób, w jaki biblioteka jest używana przez społeczność programu .NET, zmienia wpływ na istotne zmiany w deweloperach użytkowników końcowych.

- **Biblioteki niskie i średnie na poziomie** , takie jak Serializator, analizator składni HTML, mapowanie relacyjne obiektów bazy danych lub platforma internetowa, są najbardziej narażone na podstawie istotnych zmian.

  Pakiety bloków konstrukcyjnych są używane przez deweloperów użytkowników końcowych do kompilowania aplikacji i innych bibliotek jako zależności NuGet. Na przykład tworzysz aplikację i używam klienta typu open source do wywoływania usługi sieci Web. Nieprzerwana Aktualizacja zależności użytej przez klienta nie jest coś, co można naprawić. Jest to klient open-source, który musi zostać zmieniony i nie ma kontroli nad nim. Musisz znaleźć zgodne wersje bibliotek lub przesłać poprawkę do biblioteki klienta i poczekać na nową wersję. W przypadku najgorszego przypadku należy użyć dwóch bibliotek, które są zależne od wzajemnie niezgodnych wersji trzeciej biblioteki.

- **Biblioteki wysokiego poziomu** , takie jak zestaw formantów interfejsu użytkownika, są mniej wrażliwe na istotne zmiany.

  Biblioteki wysokiego poziomu są bezpośrednio przywoływane w aplikacji użytkownika końcowego. Jeśli wystąpią istotne zmiany, deweloper może zdecydować się na zaktualizowanie do najnowszej wersji lub zmodyfikować swoją aplikację, aby działała ze zmianą.

**✔️ należy** zastanowić się, jak zostanie użyta Biblioteka. Jakie skutki spowodują uszkodzenie zmian w aplikacjach i bibliotekach, które go używają?

**✔️** zminimalizować zmiany podczas tworzenia biblioteki .NET niskiego poziomu.

**✔️ rozważyć** opublikowanie poważnego ponownego zapisania biblioteki jako nowego pakietu NuGet.

## <a name="types-of-breaking-changes"></a>Typy istotnych zmian

Istotne zmiany mieszczą się w różnych kategoriach i nie wpływają na nie.

### <a name="source-breaking-change"></a>Zmiana podziału źródła

Zmiana powodująca uszkodzenie źródłowa nie ma wpływu na wykonanie programu, ale spowoduje błędy kompilacji przy następnym ponownym skompilowaniu aplikacji. Na przykład nowe Przeciążenie może utworzyć niejednoznaczność wywołań metod, które były niejednoznaczne wcześniej, lub parametr o zmienionej nazwie spowoduje przerwanie wywołań, które używają nazwanych parametrów.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Ze względu na to, że istotne zmiany w źródle są tylko szkodliwe, gdy deweloperzy ponownie skompilują swoje aplikacje, jest to najmniej zakłócona zmiana. Deweloperzy mogą łatwo naprawić swój własny uszkodzony kod źródłowy.

### <a name="behavior-breaking-change"></a>Zmiana powodująca przerwanie działania

Zmiany zachowania są najczęściej spotykanym typem zmiany: prawie każda zmiana w zachowaniu może spowodować uszkodzenie kogoś. Zmiany w bibliotece, takie jak sygnatury metod, zgłoszone wyjątki lub dane wejściowe lub wyjściowe, mogą mieć negatywny wpływ na użytkowników biblioteki. Nawet poprawka usterki może zakwalifikować się jako istotna zmiana, jeśli użytkownicy skorzystali z wcześniej naruszonych zachowań.

Dodawanie funkcji i ulepszanie nieprawidłowych zachowań jest dobrym sposobem, ale bez poważnego, aby użytkownicy mogli je uaktualnić. Jednym z rozwiązań ułatwiających deweloperom Rozwiązywanie istotnych zmian w zachowaniu zachowania jest ukrycie ich za pomocą ustawień. Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, jednocześnie wybierając opcję rezygnacji lub zrezygnowanie z istotnych zmian. Ta strategia umożliwia deweloperom zachowanie aktualności, a jednocześnie pozwala na dostosowanie kodu do swoich potrzeb.

Na przykład ASP.NET Core MVC ma koncepcję [wersji zgodności](/aspnet/core/mvc/compatibility-version) , która modyfikuje funkcje włączone i wyłączone `MvcOptions`.

**✔️ rozważyć** pozostawienie nowych funkcji domyślnie, jeśli wpływają one na istniejących użytkowników, i pozwól deweloperom na dostęp do funkcji przy użyciu ustawienia.

### <a name="binary-breaking-change"></a>Zmiana podziału binarnego

Zmiana publicznego interfejsu API biblioteki jest spowodowana zmianą w postaci binarnej, więc zestawy skompilowane pod kątem starszych wersji biblioteki nie będą już mogły wywoływania interfejsu API. Na przykład zmiana sygnatury metody przez dodanie nowego parametru spowoduje, <xref:System.MissingMethodException>że zestawy skompilowane dla starszej wersji biblioteki w celu wygenerowania.

Zmiana podziału binarnego może również spowodować przerwanie **całego zestawu**. Zmiana nazwy zestawu za pomocą `AssemblyName` spowoduje zmianę tożsamości zestawu, ponieważ spowoduje to dodanie, usunięcie lub zmianę klucza silnego nazewnictwa zestawu. Zmiana tożsamości zestawu spowoduje przerwanie całego skompilowanego kodu, który go używa.

**❌ Nie** zmieniać nazwy zestawu.

**❌ Nie** dodawaj, usuwaj ani nie zmieniaj silnego klucza nazewnictwa.

**✔️ rozważyć** użycie abstrakcyjnych klas podstawowych zamiast interfejsów.

> Dodanie niczego do interfejsu spowoduje niepowodzenie istniejących typów, które implementują go. Abstrakcyjna klasa bazowa umożliwia dodanie domyślnej implementacji wirtualnej.

**✔️ Rozważ** umieszczenie <xref:System.ObsoleteAttribute> typów i członków, które zamierzasz usunąć. Atrybut powinien zawierać instrukcje dotyczące aktualizowania kodu, aby nie używał już przestarzałego interfejsu API.

> Kod, który wywołuje typy i metody z <xref:System.ObsoleteAttribute> wygenerowaniem ostrzeżenia kompilacji z komunikatem dostarczonym do atrybutu. Ostrzeżenia umożliwiają osobom korzystającym z przestarzałego czasu powierzchni interfejsu API na Migrowanie w celu usunięcia przestarzałego interfejsu API, który nie będzie już używany.

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

**✔️ rozważyć** utrzymywanie typów i metod <xref:System.ObsoleteAttribute> w nieokreślony sposób w przypadku bibliotek niskie i średnie.

> Usuwanie interfejsów API jest uszkodzeniem binarnym. Biorąc pod uwagę przechowywanie przestarzałych typów i metod, jeśli ich utrzymanie jest niskiego kosztu i nie dodaje do biblioteki dużej liczby długów technicznych. Nieusunięcie typów i metod może pomóc w uniknięciu najgorszych przypadków wymienionych powyżej.

## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące wersji i C# aktualizacji dla deweloperów](../../csharp/whats-new/version-update-considerations.md)
- [Ostateczny Przewodnik po wprowadzeniu zmian w interfejsie API w programie .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [CoreFX reguły zmiany reguł](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Poprzednie](versioning.md)
