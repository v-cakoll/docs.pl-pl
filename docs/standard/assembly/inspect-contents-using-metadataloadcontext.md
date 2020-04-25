---
title: 'Instrukcje: inspekcja zawartości zestawu przy użyciu MetadataLoadContext'
description: Dowiedz się, jak używać MetadataLoadContext, który jest interfejsem API, który umożliwia ładowanie zestawów .NET na potrzeby inspekcji.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 90c84147c52199afc42a2efc297bc7fe40658ec7
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141199"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Instrukcje: inspekcja zawartości zestawu przy użyciu MetadataLoadContext

Interfejs API odbicia w programie .NET domyślnie umożliwia deweloperom sprawdzanie zawartości zestawów ładowanych do głównego kontekstu wykonania. Jednak czasami nie jest możliwe załadowanie zestawu do kontekstu wykonywania, na przykład ponieważ zostało skompilowane dla innej platformy lub architektury procesora lub jest [zestawem referencyjnym](reference-assemblies.md). <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> Interfejs API umożliwia ładowanie i inspekcję takich zestawów. Zestawy ładowane do programu <xref:System.Reflection.MetadataLoadContext> są traktowane jako metadane, to oznacza, że można sprawdzać typy w zestawie, ale nie można wykonać żadnego zawartego w nim kodu. W <xref:System.Reflection.MetadataLoadContext> przeciwieństwie do głównego kontekstu wykonywania, nie ładuje automatycznie zależności od bieżącego katalogu; Zamiast tego używa logiki niestandardowego powiązania dostarczonej przez <xref:System.Reflection.MetadataAssemblyResolver> przekazane do niego.

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć <xref:System.Reflection.MetadataLoadContext>programu, zainstaluj pakiet NuGet [System. odbicie. MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) . Jest on obsługiwany w dowolnej platformie docelowej zgodnej z .NET Standard 2,0, na przykład .NET Core 2,0 lub .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Utwórz MetadataAssemblyResolver dla MetadataLoadContext

Tworzenie <xref:System.Reflection.MetadataLoadContext> wymaganych wystąpień <xref:System.Reflection.MetadataAssemblyResolver>. Najprostszym sposobem na dostarczenie jednego jest użycie elementu <xref:System.Reflection.PathAssemblyResolver>, który rozwiązuje zestawy z danej kolekcji ciągów ścieżek zestawu. Ta kolekcja, oprócz zestawów, które mają być sprawdzane bezpośrednio, powinna również obejmować wszystkie wymagane zależności. Na przykład, aby odczytać atrybut niestandardowy znajdujący się w zestawie zewnętrznym, należy dołączyć ten zestaw lub wyjątek. W większości przypadków należy uwzględnić co najmniej *podstawowy zestaw*, czyli zestaw zawierający wbudowane typy systemu, takie jak <xref:System.Object?displayProperty=nameWithType>. Poniższy kod pokazuje, jak utworzyć <xref:System.Reflection.PathAssemblyResolver> przy użyciu kolekcji składającej się z skontrolowanego zestawu i bieżącego zestawu podstawowego środowiska uruchomieniowego:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Jeśli potrzebujesz dostępu do wszystkich typów BCL, możesz uwzględnić wszystkie zestawy środowiska uruchomieniowego w kolekcji. Poniższy kod pokazuje, jak utworzyć <xref:System.Reflection.PathAssemblyResolver> przy użyciu kolekcji składającej się z skontrolowanego zestawu i wszystkich zestawów bieżącego środowiska uruchomieniowego:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Utwórz MetadataLoadContext

Aby utworzyć <xref:System.Reflection.MetadataLoadContext>, wywołaj jego konstruktora <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>, przekazując poprzednio utworzony <xref:System.Reflection.MetadataAssemblyResolver> jako pierwszy parametr i podstawową nazwę zestawu jako drugi parametr. Możesz pominąć podstawową nazwę zestawu, w którym przypadku Konstruktor podejmie próbę użycia nazw domyślnych: "mscorlib", "System. Runtime" lub "Standard standardowy".

Po utworzeniu kontekstu można załadować do niego zestawy przy użyciu metod takich jak <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>. Można używać wszystkich interfejsów API odbicia w załadowanych zestawach, z wyjątkiem tych, które wymagają wykonania kodu. <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> Metoda obejmuje wykonywanie konstruktorów, dlatego należy użyć <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> metody zamiast tego, gdy konieczne jest sprawdzenie atrybutów niestandardowych w <xref:System.Reflection.MetadataLoadContext>.

Poniższy przykładowy kod tworzy <xref:System.Reflection.MetadataLoadContext>, ładuje do niego zestaw i wyprowadza atrybuty zestawu do konsoli:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Przykład

Aby uzyskać kompletny przykład kodu, zobacz [Sprawdzanie zawartości zestawu przy użyciu przykładu MetadataLoadContext](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
