---
title: 'Jak: Sprawdzanie zawartości zestawu przy użyciu metadataLoadContext'
description: Dowiedz się, jak używać MetadataLoadContext, który jest interfejsem API, który umożliwia ładowanie zestawów .NET do celów inspekcji.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: d2589d51a6e0611504c0133d293d3fdfae32553c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242663"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Jak: Sprawdzanie zawartości zestawu przy użyciu metadataLoadContext

Interfejs API odbicia w programie .NET domyślnie umożliwia deweloperom sprawdzanie zawartości zestawów załadowanych do kontekstu wykonywania głównego. Jednak czasami nie jest możliwe załadowanie zestawu do kontekstu wykonywania, na przykład, ponieważ został skompilowany dla innej platformy lub architektury procesora lub jest [to zestaw odniesienia.](reference-assemblies.md) Interfejs <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> API umożliwia ładowanie i inspekcję takich zestawów. Zestawy ładowane <xref:System.Reflection.MetadataLoadContext> do są traktowane tylko jako metadane, oznacza to, że można sprawdzić typy w zestawie, ale nie można wykonać żadnego kodu zawartego w nim. W przeciwieństwie do kontekstu <xref:System.Reflection.MetadataLoadContext> wykonywania głównego nie automatycznie załadować zależności z bieżącego katalogu; Zamiast tego używa niestandardowej logiki <xref:System.Reflection.MetadataAssemblyResolver> wiązania dostarczone przez przekazywane do niego.

## <a name="prerequisites"></a>Wymagania wstępne

Aby <xref:System.Reflection.MetadataLoadContext>użyć, należy zainstalować pakiet [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet. Jest obsługiwany na dowolnej platformie docelowej zgodnej ze standardem .NET 2.0, na przykład .NET Core 2.0 lub .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Tworzenie metadaAssemblyResolver dla MetadataLoadContext

Tworzenie <xref:System.Reflection.MetadataLoadContext> wymaga podania wystąpienia . <xref:System.Reflection.MetadataAssemblyResolver> Najprostszym sposobem, aby zapewnić jeden <xref:System.Reflection.PathAssemblyResolver>jest użycie , który rozwiązuje zestawy z danej kolekcji ciągów ścieżki zestawu. Ta kolekcja, oprócz zestawów, które chcesz sprawdzić bezpośrednio, powinny również zawierać wszystkie potrzebne zależności. Na przykład, aby odczytać atrybut niestandardowy znajduje się w zestawie zewnętrznym, należy dołączyć tego zestawu lub wyjątek zostanie zgłoszony. W większości przypadków należy dołączyć co najmniej *podstawowy zestaw*, czyli zestaw zawierający wbudowane typy systemowe, takie jak <xref:System.Object?displayProperty=nameWithType>. Poniższy kod pokazuje, <xref:System.Reflection.PathAssemblyResolver> jak utworzyć przy użyciu kolekcji składający się z sprawdzonego zestawu i bieżącego zestawu podstawowego środowiska wykonawczego:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Jeśli potrzebujesz dostępu do wszystkich typów BCL, można uwzględnić wszystkie zestawy środowiska wykonawczego w kolekcji. Poniższy kod pokazuje, <xref:System.Reflection.PathAssemblyResolver> jak utworzyć przy użyciu kolekcji składający się z sprawdzonego zestawu i wszystkie zestawy bieżącego środowiska wykonawczego:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Tworzenie metadataLoadContext

Aby utworzyć <xref:System.Reflection.MetadataLoadContext>, wywołać <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>jego konstruktora <xref:System.Reflection.MetadataAssemblyResolver> , przekazując poprzednio utworzony jako pierwszy parametr i nazwę zestawu rdzenia jako drugi parametr. Można pominąć nazwę zestawu rdzenia, w którym to przypadku konstruktor będzie próbował użyć nazw domyślnych: "mscorlib", "System.Runtime" lub "netstandard".

Po utworzeniu kontekstu można załadować do niego złożenia <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>przy użyciu metod, takich jak . Można użyć wszystkich interfejsów API odbicia na załadowanych zestawów, z wyjątkiem tych, które obejmują wykonanie kodu. Metoda <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> obejmuje wykonywanie konstruktorów, więc <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> użyj metody zamiast tego, gdy <xref:System.Reflection.MetadataLoadContext>trzeba zbadać atrybuty niestandardowe w .

Następujący przykład kodu <xref:System.Reflection.MetadataLoadContext>tworzy, ładuje do niego zestaw i wyprowadza atrybuty złożenia do konsoli:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Przykład

W przykładzie pełnego kodu zobacz [Inspekcja zawartości zestawu przy użyciu próbki MetadataLoadContext](https://github.com/dotnet/samples/tree/master/core/assembly/MetadataLoadContext).
