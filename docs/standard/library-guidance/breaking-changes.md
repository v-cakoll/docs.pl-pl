---
title: Powodująca niezgodność zmiany i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań do nawigowania między przełomowych zmian podczas tworzenia bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 83c01fdad7d836877bf692b87eeb0230219ded36
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349158"
---
# <a name="breaking-changes"></a>Fundamentalne zmiany

Jest ważne dla biblioteki .NET znaleźć równowagę między stabilności istniejących użytkowników i innowacji w przyszłości. Dowiedz się autorzy biblioteki kierunku refaktoryzacji i przemyślenie kod, dopóki nie jest doskonała, ale istotne istniejących użytkowników ma negatywnego wpływu, szczególnie w przypadku bibliotek niskiego poziomu.

## <a name="project-types-and-breaking-changes"></a>Typy projektów i fundamentalne zmiany

Jak biblioteka jest używana przez społeczność .NET zmienia efekt istotne zmiany w deweloperzy będący użytkownikami końcowymi.

* **Niski i bibliotek średnio** podobnie jak serializator, HTML analizatora, mapowania obiektowo relacyjny bazy danych lub struktury sieci web są najczęściej wykorzystywanych przez istotne zmiany.

  Bloków konstrukcyjnych pakiety są używane przez użytkowników końcowych deweloperom tworzenie aplikacji i innych bibliotek, jako zależności NuGet. Na przykład tworzysz aplikację i za pomocą klienta typu open source do wywołania usługi sieci web. Aktualizację zależności, którego klient używa na podziału nie jest coś, co można poprawić. To klient typu open source, który musi zostać zmieniona, i masz żadnej kontroli nad nim. Trzeba znaleźć zgodne wersje bibliotek lub przesłać poprawki do biblioteki klienta i poczekaj na nową wersję. Najgorszego przypadku sytuacja jest, jeśli chcesz korzystać z dwóch bibliotek, które są zależne od wzajemnie wykluczające się niezgodne wersje trzeci biblioteki.

* **Biblioteki wysokiego poziomu** takich jak pakiet interfejsu użytkownika kontrolki są mniej podatne na istotne zmiany.

  Biblioteki wysokiego poziomu odwołuje się bezpośrednio w aplikacji użytkownika końcowego. Przełomowych zmianach, deweloper może zdecydować o aktualizacji do najnowszej wersji lub mogą modyfikować ich stosowania do pracy z istotną zmianę.

**CZY ✔️** reakcji o tym, jak używać biblioteki. Jaki będzie wpływ będą miały przełomowe zmiany w aplikacji i bibliotek, które go używają?

**CZY ✔️** zminimalizować przełomowych zmianach, wdrażając bibliotekę .NET niskiego poziomu.

**ROZWAŻ ✔️** publikowanie większych Napisz ponownie jako nowy pakiet NuGet biblioteki.

## <a name="types-of-breaking-changes"></a>Typy zmian powodujących niezgodność

Powodująca niezgodność zmiany można podzielić na różne kategorie i nie są równie istotna.

### <a name="source-breaking-change"></a>Zmiana powodująca Niezgodność źródła

Zmiana powodująca niezgodność źródło nie ma wpływu na działanie programu, ale spowoduje, że błędy kompilacji podczas następnego aplikacji jest ponownie kompilowana. Na przykład też nowym przeciążeniem można utworzyć niejednoznaczność w wywołaniach metod, które wcześniej znajdowały się jednoznaczna lub zmieniono nazwę parametru spowoduje przerwanie obiektów wywołujących, które używają nazwanych parametrów.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Źródło zmiana powodująca niezgodność jest szkodliwe tylko w przypadku, gdy deweloperzy ponownie skompilować swoich aplikacji, dlatego jest najmniej szkodliwe istotną zmianę. Deweloperzy łatwo rozwiązać swój własny kod w uszkodzona źródła.

### <a name="behavior-breaking-change"></a>Zmiana powodująca niezgodność zachowanie

Zmiany zachowania są najczęściej spotykanym typem istotnej zmiany: praktycznie dowolne zmiany w zachowaniu może spowodować przerwanie osoby. Zmiany do biblioteki, takie jak podpisy metod wyjątki zgłaszane lub wejścia lub wyjścia formatów danych mogą wszystkie niekorzystnie wpłynąć na klientów biblioteki. Nawet poprawki mogą zakwalifikować się do istotnej zmiany, jeśli użytkownicy opiera się na zachowanie wcześniej przerwane.

Dodawanie funkcji i poprawianie nieprawidłowych zachowań jest to przydatne, ale bez obsługi może być bardzo trudne dla istniejących użytkowników do uaktualnienia. Jedno z podejść do pomagając deweloperom postępowania z zachowaniem przełomowych zmian jest je ukryć za ustawienia. Ustawienia umożliwiają deweloperom aktualizację do najnowszej wersji biblioteki, w tym samym czasie, wybierając zgoda lub zrezygnować z istotne zmiany. Ta strategia umożliwia deweloperom bądź na bieżąco, pozwalając na ich kod konsumencki dostosowania wraz z upływem czasu.

Na przykład, ASP.NET Core MVC korzysta z koncepcji [zgodność wersji](/aspnet/core/mvc/compatibility-version) funkcje włączone i wyłączone, który modyfikuje `MvcOptions`.

**ROZWAŻ ✔️** opuszczania nowe funkcje domyślnie, jeśli one wpływu na istniejących użytkowników i umożliwiają deweloperom Zezwól na korzystanie z funkcji z ustawieniem.

### <a name="binary-breaking-change"></a>Zmiana powodująca niezgodność binarne

Zmiana powodująca niezgodność plik binarny się dzieje, gdy zmienisz publiczny interfejs API biblioteki, dzięki czemu zestawy skompilowane starsze wersje biblioteki nie jest już możliwe do wywołania interfejsu API. Na przykład zmiana sygnatury metody przez dodanie nowego parametru spowoduje, że zestawy skompilowane starszą wersję biblioteki throw <xref:System.MissingMethodException>.

Zmiana powodująca niezgodność plik binarny może to również uszkodzenie **cały zespół**. Zmiana nazwy zestawu za pomocą `AssemblyName` ulegnie zmianie tożsamości zestawu, podobnie jak dodawanie, usuwanie i zmienianie silnego klucza nazw zestawu. Zmiana tożsamości zestawu spowoduje przerwanie wszystkich skompilowany kod, który korzysta z niego.

**❌ NIE** Zmień nazwę zestawu.

**❌ NIE** dodać, usunąć lub zmienić silnego klucza nazewnictwa.

**ROZWAŻ ✔️** przy użyciu abstrakcyjnych klas bazowych, zamiast interfejsów.

> Dodawanie niczego do interfejsu spowoduje, że istniejące typy implementujące nie powiedzie się. Abstrakcyjna klasa bazowa umożliwia dodawanie Domyślna implementacja wirtualnego.

**ROZWAŻ ✔️** umieszczenie <xref:System.ObsoleteAttribute> na typy i elementy członkowskie, które zamierzasz usunąć. Ten atrybut powinien mieć instrukcje dotyczące aktualizowania kodu nie są już używane przestarzałych API.

> Kod, który wywołuje typy i metody o <xref:System.ObsoleteAttribute> zostanie wygenerowane ostrzeżenie dotyczące kompilacji za pomocą wiadomości podano do atrybutu. Osoby zapewniają ostrzeżeń, które umożliwia migracji po usunięciu przestarzałe API większość nie są już przestarzałe czasu powierzchni interfejsu API przy użyciu go.

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

## <a name="see-also"></a>Zobacz także

* [Wersja i zaktualizuj uwagi dla deweloperów języka C#](../../csharp/whats-new/version-update-considerations.md)
* [Ostateczny przewodnik dotyczący interfejsu API — przełomowe zmiany w .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
* [CoreFX istotnej zmiany zasad](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
[Poprzednie](./versioning.md)
