---
title: Przełomowe zmiany i biblioteki .NET
description: Najlepsze zalecenia dotyczące nawigowania po zmianach podczas tworzenia bibliotek .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400422"
---
# <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Ważne jest, aby biblioteka .NET znalazła równowagę między stabilnością dla istniejących użytkowników a innowacjami na przyszłość. Autorzy biblioteki skłaniają się ku refaktoryzacji i ponownemu myśleniu kodu, dopóki nie będzie on doskonały, ale złamanie istniejących użytkowników ma negatywny wpływ, szczególnie w przypadku bibliotek niskiego poziomu.

## <a name="project-types-and-breaking-changes"></a>Typy projektów i zmiany dotyczące najpoławów

Sposób, w jaki biblioteka jest używana przez społeczność .NET zmienia wpływ wprowadzania zmian na deweloperów użytkowników końcowych.

- **Biblioteki niskiego i średniego poziomu, takie** jak serializator, analizator HTML, obiekt bazy danych relacyjny maper lub struktura sieci web, są najbardziej dotknięte przez zmiany łamiące.

  Pakiety bloków konstrukcyjnych są używane przez deweloperów użytkowników końcowych do tworzenia aplikacji i przez inne biblioteki jako zależności NuGet. Na przykład budujesz aplikację i używasz klienta open source do wywołania usługi sieci web. Aktualizacja podziału zależności, której używa klient, nie jest czymś, co można naprawić. Jest to klient open-source, który musi zostać zmieniony i nie masz nad nim kontroli. Musisz znaleźć zgodne wersje bibliotek lub przesłać poprawkę do biblioteki klienta i poczekać na nową wersję. Najgorszą sytuacją jest, jeśli chcesz użyć dwóch bibliotek, które zależą od wzajemnie niezgodnych wersji trzeciej biblioteki.

- **Biblioteki wysokiego poziomu,** takie jak zestaw formantów interfejsu użytkownika, są mniej wrażliwe na przełomowe zmiany.

  Biblioteki wysokiego poziomu są bezpośrednio odwołuje się w aplikacji użytkownika końcowego. Jeśli wystąpią zmiany dotyczące łamania, deweloper może zaktualizować do najnowszej wersji lub zmodyfikować swoją aplikację do pracy ze zmianą podziału.

✔️ zastanów się, w jaki sposób będzie używana twoja biblioteka. Jaki wpływ będą miały zmiany krytyczne na aplikacje i biblioteki, które go używają?

✔️ zminimalizować zmiany podczas tworzenia biblioteki .NET niskiego poziomu.

✔️ ROZWAŻ opublikowanie głównych przepisać biblioteki jako nowy pakiet NuGet.

## <a name="types-of-breaking-changes"></a>Rodzaje przełomowych zmian

Zmiany przełamywania dzielą się na różne kategorie i nie są równie ważne.

### <a name="source-breaking-change"></a>Zmiana podziału źródła

Zmiana podziału źródła nie wpływa na wykonanie programu, ale spowoduje błędy kompilacji przy następnym ponownym skompilowaniu aplikacji. Na przykład nowe przeciążenie można utworzyć niejednoznaczności w wywołaniach metody, które były wcześniej jednoznaczne lub zmieniony parametr spowoduje przerwanie wywołujących, które używają nazwanych parametrów.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Ponieważ zmiana podziału źródła jest szkodliwa tylko wtedy, gdy deweloperzy ponownie skompilować swoje aplikacje, jest to najmniej uciążliwa zmiana podziału. Deweloperzy mogą łatwo naprawić swój własny uszkodzony kod źródłowy.

### <a name="behavior-breaking-change"></a>Zmiana łamania zachowań

Zmiany zachowania są najczęstszym typem zmiany podziału: prawie każda zmiana w zachowaniu może kogoś złamać. Zmiany w bibliotece, takie jak podpisy metod, wyjątki generowane lub formaty danych wejściowych lub wyjściowych, mogą mieć negatywny wpływ na konsumentów biblioteki. Nawet poprawka błędu może kwalifikować się jako przełomowa zmiana, jeśli użytkownicy polegali na wcześniej złamanym zachowaniu.

Dodawanie funkcji i poprawa złych zachowań jest dobrą rzeczą, ale bez opieki może to bardzo utrudnić istniejącym użytkownikom uaktualnienie. Jednym z podejść do pomagania deweloperom radzić sobie ze zmianami łamania zachowań jest ukrycie ich za ustawieniami. Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, jednocześnie decydując się na opcję wyrażenia zgody lub rezygnację z łamania zmian. Ta strategia pozwala deweloperom być na bieżąco, pozwalając im czasowy dostosowywać kod.

Na przykład ASP.NET Core MVC ma pojęcie [wersji zgodności,](/aspnet/core/mvc/compatibility-version) która modyfikuje `MvcOptions`funkcje włączone i wyłączone na .

✔️ ROZWAŻ pozostawienie nowych funkcji domyślnie wyłączonych, jeśli mają one wpływ na istniejących użytkowników, i pozwól deweloperom wyrazić zgodę na tę funkcję z ustawieniem.

### <a name="binary-breaking-change"></a>Zmiana podziału binarnego

Binarna zmiana podziału występuje po zmianie publicznego interfejsu API biblioteki, więc zestawy skompilowane ze starszymi wersjami biblioteki nie są już w stanie wywołać interfejsu API. Na przykład zmiana podpisu metody przez dodanie nowego parametru spowoduje, że zestawy skompilowane ze starszą wersją biblioteki będą wyrzucać . <xref:System.MissingMethodException>

Zmiana podziału binarnego może również przerwać **cały zestaw**. Zmiana nazwy zestawu `AssemblyName` z zmieni tożsamość zestawu, jak będzie dodawanie, usuwanie lub zmienianie zestawu silny klucz nazewnictwa. Zmiana tożsamości zestawu spowoduje przerwanie całego skompilowanego kodu, który go używa.

❌NIE zmieniaj nazwy zestawu.

❌NIE dodawaj, NIE usuwaj ani nie zmieniaj silnego klucza nazewnictwa.

✔️ ROZWAŻ UŻYCIE abstrakcyjnych klas podstawowych zamiast interfejsów.

> Dodawanie czegokolwiek do interfejsu spowoduje, że istniejące typy, które implementują go nie powiedzie się. Abstrakcyjna klasa podstawowa umożliwia dodanie domyślnej implementacji wirtualnej.

✔️ ROZWAŻ <xref:System.ObsoleteAttribute> umieszczenie na typy i elementy członkowskie, które zamierzasz usunąć. Atrybut powinien mieć instrukcje dotyczące aktualizowania kodu, aby nie używać przestarzałego interfejsu API.

> Kod, który wywołuje typy <xref:System.ObsoleteAttribute> i metody z wygeneruje ostrzeżenie kompilacji z komunikatem dostarczonym do atrybutu. Ostrzeżenia dają ludziom, którzy używają przestarzałego czasu powierzchni interfejsu API do migracji, tak aby po usunięciu przestarzałego interfejsu API większość z niego nie używa.

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

✔️ NALEŻY ROZWAŻYĆ prowadzenie <xref:System.ObsoleteAttribute> typów i metod z inczasanie w bibliotekach niskiego i średniego poziomu.

> Usuwanie interfejsów API jest binarną zmianą podziału. Biorąc pod uwagę utrzymanie przestarzałych typów i metod, jeśli ich utrzymanie jest niski koszt i nie dodaje wiele długu technicznego do biblioteki. Nie usunięcie typów i metod może pomóc uniknąć najgorszych scenariuszy wymienionych powyżej.

## <a name="see-also"></a>Zobacz też

- [Zagadnienia dotyczące wersji i aktualizacji dla deweloperów języka C#](../../csharp/whats-new/version-update-considerations.md)
- [Ostateczny przewodnik po zmianach łamania interfejsu API w .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [Reguły łamania zmian .NET](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Wstecz](versioning.md)
