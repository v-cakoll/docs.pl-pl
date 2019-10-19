---
title: Zestawy odwołań
description: Dowiedz się więcej na temat zestawów referencyjnych, specjalnego typu zestawów w programie .NET, które zawierają tylko publiczną powierzchnię interfejsu API biblioteki
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: f509397f5cb48a004b800014b2b071721e0d68b8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582846"
---
# <a name="reference-assemblies"></a>Zestawy odwołań

*Zestawy referencyjne* są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganą do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich składowych, które są istotne w przypadku odwoływania się do zestawu w narzędziach kompilacji (w związku z czym nazwa), ale wyklucza wszystkie implementacje składowe, a także deklaracje członków prywatnych, którzy nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Z kolei regularne zestawy są nazywane *zestawami implementacji*. 

Nie można załadować zestawów referencyjnych do wykonania, ale mogą one być przesyłane jako dane wejściowe kompilatora w taki sam sposób jak zestawy implementacji. Zestawy referencyjne są zwykle dystrybuowane z zestawem Software Development Kit (SDK) określonej platformy lub biblioteki, specjalny składnik oprogramowania instalowany tylko na komputerach deweloperskich.

Użycie zestawu referencyjnego umożliwia deweloperom tworzenie programów przeznaczonych dla określonej wersji biblioteki bez konieczności używania pełnego zestawu implementacji dla tej wersji. Załóżmy, że masz tylko najnowszą wersję niektórych bibliotek na swojej maszynie, ale chcesz skompilować program przeznaczony dla maszyny z wcześniejszą wersją tej biblioteki. Jeśli kompilujesz bezpośrednio względem zestawu implementacji, możesz przypadkowo użyć elementów członkowskich interfejsu API, które nie są dostępne we wcześniejszej wersji, a podczas testowania programu na maszynie docelowej będzie można znaleźć tylko ten błąd. Jeśli kompilujesz względem zestawu odwołań dla starszej wersji, natychmiast otrzymasz błąd w czasie kompilacji.

Ponadto zestaw referencyjny może reprezentować kontrakt, czyli zestaw interfejsów API, które nie odpowiadają zestawowi konkretnych implementacji. Taki zestaw referencyjny, nazywany *zestawem kontraktu*, może służyć jako ukierunkowana na wiele platform, które obsługują ten sam zestaw interfejsów API. Na przykład .NET Standard zawiera zestaw kontraktu, *plik. dll*, który reprezentuje zestaw wspólnych interfejsów API współużytkowanych przez różne platformy .NET. Implementacje tych interfejsów API są zawarte w różnych zestawach na różnych platformach, takich jak *mscorlib. dll* w .NET Framework lub *System. private. CoreLib. dll* na platformie .NET Core. Biblioteka, która jest przeznaczona dla .NET Standard można uruchamiać na wszystkich platformach, które obsługują .NET Standard. 

## <a name="using-reference-assemblies"></a>Używanie zestawów odwołań

Aby używać niektórych interfejsów API z projektu, należy dodać odwołania do ich zestawów. Można dodać odwołania do zestawów implementacji bezpośrednio lub do zestawów referencyjnych. Zdecydowanie zalecamy używanie zestawów referencyjnych, gdy są one dostępne, ponieważ takie działanie gwarantuje, że używasz tylko elementów członkowskich interfejsu API, które są obsługiwane w wersji docelowej i są przeznaczone do użytku przez projektantów interfejsów API (innymi słowy, nie podejmują zależności na temat szczegółów implementacji).

Zestawy referencyjne dla bibliotek .NET Framework są dystrybuowane z pakietami docelowymi. Można je uzyskać, pobierając Autonomiczny Instalator lub wybierając składnik w Instalatorze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Install the .NET Framework for Developers](../../framework/install/guide-for-developers.md). W przypadku platformy .NET Core i .NET Standard zestawy odwołań są automatycznie pobierane zgodnie z potrzebami (za pośrednictwem NuGet) i przywoływane. W przypadku platformy .NET Core 3,0 lub nowszej zestawy referencyjne dla podstawowej platformy są w pakiecie [Microsoft. servicecore. app. ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (w zamian jest używany pakiet [Microsoft. servicecore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) ) dla wersji przed 3,0. Aby uzyskać więcej informacji, zobacz [pakiety, aplikacje i struktury](../../core/packages.md) w przewodniku .NET Core.

Po dodaniu odwołań do zestawów .NET Framework w programie Visual Studio przy użyciu okna dialogowego **Dodawanie odwołania** można wybrać zestaw z listy, a program Visual Studio automatycznie odnajdzie zestawy referencyjne odpowiadające wersji platformy docelowej wybrane w projekcie. To samo dotyczy dodawania odwołań bezpośrednio do projektu MSBuild przy użyciu elementu projektu [referencyjnego](/visualstudio/msbuild/common-msbuild-project-items#reference) : należy określić tylko nazwę zestawu, a nie pełną ścieżkę pliku. Po dodaniu odwołań do tych zestawów w wierszu polecenia przy użyciu opcji kompilatora `-reference` ([w C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) i w [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) lub przy użyciu metody <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> w interfejsie API Roslyn należy ręcznie określić pliki zestawu odwołań dla poprawna wersja platformy docelowej. Pliki zestawów odwołań .NET Framework znajdują się w *zestawach% ProgramFiles (x86)% \\Reference \\Microsoft \\Framework \\. NETFramework* . W przypadku platformy .NET Core można wymusić operację publikowania, aby skopiować zestawy referencyjne dla platformy docelowej do podkatalogu *Publish/ReFS* w katalogu wyjściowym przez ustawienie właściwości projektu `PreserveCompilationContext` na `true`. Następnie można przekazać te pliki zestawu odwołań do kompilatora. Używanie `DependencyContext` z pakietu [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) może pomóc w znalezieniu ich ścieżek.

Ponieważ nie zawierają one implementacji, nie można załadować zestawów odwołań do wykonania; podjęto próbę wykonania tej czynności w <xref:System.BadImageFormatException?displayProperty=nameWithType>. Jednak nadal mogą być ładowane do kontekstu tylko odbicie (przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>), jeśli trzeba będzie przeanalizować ich zawartość.

## <a name="generating-reference-assemblies"></a>Generowanie zestawów referencyjnych

Generowanie zestawów referencyjnych dla bibliotek może być przydatne, gdy klienci biblioteki często muszą kompilować swoje programy w wielu różnych wersjach biblioteki (to jest, gdy zachodzi potrzeba wdrożenia funkcji podobnej do .NET Framework pakietów docelowych wymienione powyżej dla własnego projektu). Dystrybuowanie zestawów implementacji dla wszystkich tych wersji może być niepraktyczne ze względu na ich duży rozmiar. Zestawy referencyjne są mniejsze w rozmiarze, więc dystrybuowanie ich jako części zestawu SDK biblioteki zmniejsza rozmiar pobierania i oszczędza miejsce na dysku.

Narzędzia środowisk IDE i Build Tools mogą również korzystać z zestawów referencyjnych, aby skrócić czasy kompilacji w przypadku dużych rozwiązań składających się z wielu bibliotek klas. Zwykle w scenariuszach kompilacji przyrostowej projekt jest odbudowany, gdy którykolwiek z jego plików wejściowych zostanie zmieniony, włącznie z zestawami, od których zależy. Zestaw implementacji zmienia się za każdym razem, gdy programista zmieni implementację dowolnego elementu członkowskiego. Zestaw referencyjny zmienia się tylko wtedy, gdy jego publiczny interfejs API ma wartość. W związku z tym, użycie zestawu odwołania jako pliku wejściowego zamiast zestawu implementacji pozwala pominąć kompilację zależnego projektu w niektórych przypadkach. 

Można generować zestawy referencyjne:

- W projekcie MSBuild, przy użyciu [właściwości projektu `ProduceReferenceAssembly`](/visualstudio/msbuild/common-msbuild-project-properties).
- Podczas kompilowania programu z wiersza polecenia, przez specifiying `-refonly`[( C#w ](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) lub `-refout` ([ C#w ](../../csharp/language-reference/compiler-options/refout-compiler-option.md), [w Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) opcji kompilatora.
- W przypadku korzystania z interfejsu API Roslyn przez ustawienie <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> na `true` i <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> do `false` w obiekcie przekazaną do metody <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType>.

Jeśli chcesz dystrybuować zestawy referencyjne z pakietami NuGet, musisz uwzględnić je w podkatalogu *ref \\* w katalogu pakietu, a nie w podkatalogu *lib \\* używanym do zestawów implementacji.

## <a name="reference-assemblies-structure"></a>Struktura zestawów odwołań

Zestawy referencyjne są rozwinięciem powiązanej koncepcji, *zestawów samych metadanych*. Zestawy zawierające tylko metadane są zastępowane przez jedną `throw null` treść, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Powód używania `throw null`ych treści (w przeciwieństwie do braku treści) polega na tym, że PEVerify może działać i przekazywać (w związku z tym sprawdzanie kompletności metadanych).

Zestawy referencyjne usuwają metadane (prywatne składowe) z zestawów samych metadanych:

- Zestaw odniesienia zawiera odwołania do potrzebnych elementów interfejsu API. Rzeczywisty zestaw może zawierać dodatkowe odwołania dotyczące konkretnych implementacji. Na przykład zestaw odwołania dla `class C { private void M() { dynamic d = 1; ... } }` nie odwołuje się do żadnego typu wymaganego dla `dynamic`.
- Prywatne funkcje — elementy członkowskie (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu na kompilację. Jeśli nie ma żadnych atrybutów [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) , składowe funkcji wewnętrznych również są usuwane.

Metadane w zestawach referencyjnych nadal zachowują informacje o następujących kwestiach:

- Wszystkie typy, w tym typy prywatne i zagnieżdżone.
- Wszystkie atrybuty, nawet wewnętrzne.
- Wszystkie metody wirtualne.
- Jawne implementacje interfejsu. 
- Jawnie zaimplementowane właściwości i zdarzenia, ponieważ ich metody dostępu są wirtualne.
- Wszystkie pola struktur. 

Zestawy referencyjne zawierają atrybut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na poziomie zestawu. Ten atrybut może być określony w źródle; Następnie kompilator nie będzie musiał go przeprowadzić. Ze względu na ten atrybut środowiska uruchomieniowe będą odrzucać ładowanie zestawów odwołań do wykonania (ale nadal mogą być ładowane w trybie tylko odbicie).

Dokładne szczegóły struktury zestawu odwołań zależą od wersji kompilatora. Nowsze wersje mogą zdecydować się na wykluczenie większej liczby metadanych, jeśli zostanie ona określona jako nie wpływająca na publiczną powierzchnię interfejsu API.

> [!NOTE]
> Informacje w tej sekcji dotyczą tylko zestawów referencyjnych wygenerowanych przez kompilatory Roslyn zaczynające się od C# wersji 7,1 lub Visual Basic wersji 15,3. Struktura zestawów referencyjnych dla bibliotek .NET Framework i .NET Core może różnić się w niektórych szczegółach, ponieważ korzystają z własnego mechanizmu generowania zestawów odwołań. Na przykład mogą mieć całkowicie puste treści metody zamiast treści `throw null`. Jednak ogólna zasada nadal stosuje się: nie mają one przydatnych implementacji metod i zawierają tylko metadane dla elementów członkowskich, które mają zauważalny wpływ z perspektywy publicznego interfejsu API.

## <a name="see-also"></a>Zobacz także

- [Zestawy w środowisku .NET](index.md)
- [Program z zestawami](program.md)
- [Omówienie określania celu platformy](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
