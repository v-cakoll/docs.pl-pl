---
title: Odwoływanie się do zestawów
description: Dowiedz się więcej o zestawach odwołań, specjalnym typie zestawów w .NET, które zawierają tylko publiczną powierzchnię interfejsu API biblioteki
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141071"
---
# <a name="reference-assemblies"></a>Odwoływanie się do zestawów

*Zestawy odwołań* są specjalnym typem zestawu, który zawiera tylko minimalną ilość metadanych wymaganych do reprezentowania publicznej powierzchni interfejsu API biblioteki. Obejmują one deklaracje dla wszystkich elementów członkowskich, które są istotne podczas odwoływania się do zestawu w narzędziakompilacji, ale wykluczają wszystkie implementacje elementów członkowskich i deklaracje prywatnych elementów członkowskich, które nie mają zauważalnego wpływu na ich kontrakt interfejsu API. Natomiast regularne zestawy są nazywane *zestawami implementacji*.

Zestawy odwołań nie można załadować do wykonania, ale mogą być przekazywane jako dane wejściowe kompilatora w taki sam sposób jak zestawy implementacji. Zestawy referencyjne są zwykle dystrybuowane za pomocą zestawu SDK (Software Development Kit) określonej platformy lub biblioteki.

Za pomocą zestawu odniesienia umożliwia deweloperom tworzenie programów, które są przeznaczone dla określonej wersji biblioteki bez konieczności pełnego zestawu implementacji dla tej wersji. Załóżmy, że masz tylko najnowszą wersję niektórych biblioteki na komputerze, ale chcesz utworzyć program, który jest przeznaczony dla wcześniejszej wersji tej biblioteki. Jeśli skompilować bezpośrednio względem zestawu implementacji, może przypadkowo użyć elementów członkowskich interfejsu API, które nie są dostępne we wcześniejszej wersji. Ten błąd znajdziesz tylko podczas testowania programu na komputerze docelowym. Jeśli skompilować względem zestawu odwołania dla wcześniejszej wersji, natychmiast otrzymasz błąd czasu kompilacji.

Zestaw odniesienia może również reprezentować kontrakt, czyli zestaw interfejsów API, które nie odpowiadają konkretnemu zestawowi implementacji. Takie zestawy odwołań, nazywane *zestawem kontraktu,* mogą być używane do obsługi wielu platform obsługujących ten sam zestaw interfejsów API. Na przykład .NET Standard udostępnia zestaw kontraktu *netstandard.dll*, który reprezentuje zestaw typowych interfejsów API współużytkowane między różnymi platformami .NET. Implementacje tych interfejsów API są zawarte w różnych zestawach na różnych platformach, takich jak *mscorlib.dll* na .NET Framework lub *System.Private.CoreLib.dll* na .NET Core. Biblioteka przeznaczona dla programu .NET Standard może być uruchamiana na wszystkich platformach obsługujących standard .NET.

## <a name="using-reference-assemblies"></a>Korzystanie z zestawów odwołań

Aby użyć niektórych interfejsów API z projektu, należy dodać odwołania do ich zestawów. Można dodać odwołania do zestawów implementacji lub do zestawów odwołań. Zaleca się używanie zestawów odwołań, gdy są one dostępne. W ten sposób zapewnia, że używasz tylko obsługiwane elementy członkowskie interfejsu API w wersji docelowej, przeznaczone do użycia przez projektantów interfejsu API. Przy użyciu zestawu odwołania zapewnia, że nie bierzesz zależności od szczegółów implementacji.

Zestawy odwołań dla bibliotek .NET Framework są dystrybuowane z pakietami określania wartości docelowej. Można je uzyskać, pobierając instalator autonomiczny lub wybierając składnik w instalatorze programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie platformy .NET Framework dla deweloperów](../../framework/install/guide-for-developers.md). W przypadku .NET Core i .NET Standard zestawy odwołań są automatycznie pobierane w razie potrzeby (za pośrednictwem NuGet) i odwołuje się do. W przypadku programu .NET Core 3.0 lub nowszego zestawy odwołań dla podstawowej struktury znajdują się w pakiecie [Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (pakiet [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) jest używany zamiast tego dla wersji przed 3.0). Aby uzyskać więcej informacji, zobacz [pakiety, metapakiety i struktury](../../core/packages.md) w przewodniku .NET Core.

Po dodaniu odwołań do zestawów programu .NET Framework w programie Visual Studio przy użyciu okna **dialogowego Dodawanie odwołania** wybierz zestaw z listy, a program Visual Studio automatycznie znajdzie zestawy odwołań odpowiadające docelowej wersji struktury wybranej w projekcie. To samo dotyczy dodawania odwołań bezpośrednio do projektu MSBuild przy użyciu elementu projektu [odwołania:](/visualstudio/msbuild/common-msbuild-project-items#reference) należy tylko określić nazwę zestawu, a nie pełną ścieżkę pliku. Podczas dodawania odwołań do tych zestawów w `-reference` wierszu polecenia przy użyciu opcji kompilatora[(w języku C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) i [Visual Basic)](../../visual-basic/reference/command-line-compiler/reference.md)lub przy użyciu <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> metody w interfejsie API Roslyn, należy ręcznie określić pliki zestawu odwołań dla poprawnej wersji platformy docelowej. Pliki referencyjne zestawu .NET Framework znajdują się w *%ProgramFiles(x86)%\\zestawach\\referencyjnych Microsoft\\Framework\\. katalog NETFramework.* W przypadku programu .NET Core można wymusić operację publikowania, aby skopiować zestawy odwołań `PreserveCompilationContext` dla platformy docelowej do podkatalogu *publikowania/refs* katalogu wyjściowego, ustawiając właściwość projektu na `true`. Następnie można przekazać te pliki zestawu odwołania do kompilatora. Korzystanie `DependencyContext` z [pakietu Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) może pomóc zlokalizować ich ścieżki.

Ponieważ nie zawierają one implementacji, zestawów odwołań nie można załadować do wykonania. Próba zrobienia tego powoduje <xref:System.BadImageFormatException?displayProperty=nameWithType>. Jeśli chcesz sprawdzić zawartość zestawu odwołania, można załadować go do kontekstu tylko do odbicia <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> w .NET <xref:System.Reflection.MetadataLoadContext> Framework (przy użyciu metody) lub w .NET Core.

## <a name="generating-reference-assemblies"></a>Generowanie zestawów odwołań

Generowanie zestawów odwołań dla bibliotek może być przydatne, gdy użytkownicy biblioteki muszą tworzyć swoje programy w wielu różnych wersjach biblioteki. Dystrybucja zestawów implementacji dla wszystkich tych wersji może być niepraktyczne ze względu na ich duży rozmiar. Zestawy odwołań mają mniejszy rozmiar, a ich dystrybucja jako część pliku SDK biblioteki zmniejsza rozmiar pobierania i oszczędza miejsce na dysku.

IDEs i narzędzia kompilacji również można korzystać z zestawów odwołań, aby skrócić czas kompilacji w przypadku dużych rozwiązań składających się z wielu bibliotek klas. Zazwyczaj w scenariuszach kompilacji przyrostowej projekt jest przebudowywany po zmianie dowolnego z jego plików wejściowych, w tym zestawów, od których zależy. Zestaw implementacji zmienia się za każdym razem, gdy programista zmienia implementację dowolnego elementu członkowskiego. Zestaw odniesienia zmienia się tylko wtedy, gdy ma to wpływ na jego publiczny interfejs API. Dlatego przy użyciu zestawu odniesienia jako pliku wejściowego zamiast zestawu implementacji umożliwia pomijanie kompilacji projektu zależnego w niektórych przypadkach.

Można wygenerować zestawy odwołań:

- W projekcie MSBuild przy użyciu [ `ProduceReferenceAssembly` właściwości projektu](/visualstudio/msbuild/common-msbuild-project-properties).
- Podczas kompilowania programu z wiersza polecenia, `-refonly` przez specifiying[(C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / [Visual Basic)](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) lub `-refout` [(C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / Visual[Basic)](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)opcje kompilatora.
- Podczas korzystania z interfejsu API <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> `true` Roslyn, ustawiając do i <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> do `false` w obiekcie przekazywane do <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> metody.

Jeśli chcesz rozpowszechniać zestawy odwołań z pakietami NuGet, należy je uwzględnić w podkatalogu *ref\\ * pod katalogiem pakietów, a nie w podkatalogu *lib\\ * używanym do zestawów implementacji.

## <a name="reference-assemblies-structure"></a>Struktura złożeń referencyjnych

Zestawy odwołań są rozszerzeniem pokrewnej koncepcji, *zestawów tylko metadanych*. Zestawy tylko do metadanych mają swoje `throw null` treści metody zastąpione jednym treścią, ale obejmują wszystkie elementy członkowskie z wyjątkiem typów anonimowych. Powodem używania `throw null` obiektów (w przeciwieństwie do żadnych obiektów) jest tak, aby **PEVerify** można uruchomić i przekazać (w ten sposób sprawdzania poprawności kompletności metadanych).

Zestawy odwołań dodatkowo usuwają metadane (elementy członkowskie prywatne) z zestawów tylko do metadanych:

- Zestaw odniesienia ma tylko odwołania do tego, czego potrzebuje na powierzchni interfejsu API. Rzeczywisty zestaw może mieć dodatkowe odwołania związane z określonymi implementacjami. Na przykład zestaw odniesienia `class C { private void M() { dynamic d = 1; ... } }` dla nie odwołuje się `dynamic`do żadnych typów wymaganych dla .
- Prywatne elementy członkowskie funkcji (metody, właściwości i zdarzenia) są usuwane w przypadkach, gdy ich usunięcie nie ma zauważalnego wpływu kompilacji. Jeśli nie ma żadnych [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) atrybutów, elementy członkowskie funkcji wewnętrznych są również usuwane.

Metadane w zestawach odwołań nadal zachowują następujące informacje:

- Wszystkie typy, w tym typy prywatne i zagnieżdżone.
- Wszystkie atrybuty, nawet wewnętrzne.
- Wszystkie metody wirtualne.
- Jawne implementacje interfejsu.
- Jawnie zaimplementowane właściwości i zdarzenia, ponieważ ich akcesory są wirtualne.
- Wszystkie pola struktur.

Zestawy odwołań zawierają atrybut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na poziomie zestawu. Ten atrybut może być określony w źródle; następnie kompilator nie będzie musiał go syntetyzować. Ze względu na ten atrybut, uruchamianie odmówi załadować zestawów odwołań do wykonania (ale mogą być ładowane w trybie tylko do odbicia).

Szczegóły dokładnej struktury zestawu odwołania zależą od wersji kompilatora. Nowsze wersje mogą wykluczyć więcej metadanych, jeśli zostanie określony jako niewpływające na publiczną powierzchnię interfejsu API.

> [!NOTE]
> Informacje w tej sekcji mają zastosowanie tylko do zestawów referencyjnych generowanych przez kompilatory Roslyn począwszy od wersji C# 7.1 lub Visual Basic w wersji 15.3. Struktura zestawów odwołań dla bibliotek .NET Framework i .NET Core może się różnić w niektórych szczegółach, ponieważ używają własnego mechanizmu generowania zestawów odwołań. Na przykład mogą mieć całkowicie puste obiekty `throw null` metody zamiast treści. Ale ogólna zasada nadal ma zastosowanie: nie mają implementacji metod użytkowych i zawierają metadane tylko dla członków, które mają zauważalny wpływ z perspektywy publicznego interfejsu API.

## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](index.md)
- [Przegląd kierowania ramowego](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
