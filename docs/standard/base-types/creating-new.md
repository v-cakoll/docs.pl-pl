---
title: Tworzenie nowych ciągów w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103819"
---
# <a name="creating-new-strings-in-net"></a>Tworzenie nowych ciągów w .NET
.NET Framework umożliwia ciągi do utworzenia przy użyciu prostego przypisania, a także przeciążenia konstruktora klasy do obsługi tworzenia ciągów przy użyciu wielu różnych parametrów. .NET Framework udostępnia również kilka <xref:System.String?displayProperty=nameWithType> metod w klasie, które tworzą nowe obiekty ciągu, łącząc kilka ciągów, tablicciągów lub obiektów.  
  
## <a name="creating-strings-using-assignment"></a>Tworzenie ciągów przy użyciu przypisania  
 Najprostszym sposobem utworzenia <xref:System.String> nowego obiektu jest po prostu <xref:System.String> przypisać literał ciągu do obiektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Tworzenie ciągów przy użyciu konstruktora klas  
 Można użyć przeciążenia <xref:System.String> konstruktora klasy do tworzenia ciągów z tablic znaków. Można również utworzyć nowy ciąg, powielając określony znak określoną liczbę razy.  
  
## <a name="methods-that-return-strings"></a>Metody, które zwracają ciągi  
 W poniższej tabeli wymieniono kilka przydatnych metod, które zwracają nowe obiekty ciągu.  
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Tworzy sformatowany ciąg z zestawu obiektów wejściowych.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Tworzy ciągi z dwóch lub więcej ciągów.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Tworzy nowy ciąg, łącząc tablicę ciągów.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Tworzy nowy ciąg, wstawiając ciąg do określonego indeksu istniejącego ciągu.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Kopiuje określone znaki w ciągu do określonej pozycji w tablicy znaków.|  
  
### <a name="format"></a>Format  
 Za pomocą metody **String.Format** można tworzyć sformatowane ciągi i łączenie ciągów reprezentujących wiele obiektów. Ta metoda automatycznie konwertuje dowolny przekazany obiekt na ciąg. Na przykład jeśli aplikacja musi wyświetlać wartość **Int32** i **DateTime** wartość dla użytkownika, można łatwo skonstruować ciąg do reprezentowania tych wartości przy użyciu **Format** metody. Aby uzyskać informacje na temat konwencji formatowania używanych z tą metodą, zobacz sekcję [dotyczącą formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).  
  
 W poniższym przykładzie użyto **Metody Format** do utworzenia ciągu, który używa zmiennej całkowitej.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 W tym<xref:System.DateTime.Now%2A?displayProperty=nameWithType> przykładzie wyświetla bieżącą datę i godzinę w sposób określony przez kulturę skojarzoną z bieżącym wątkiem.  
  
### <a name="concat"></a>Concat  
 **String.Concat** Metoda może służyć do łatwego tworzenia nowego obiektu ciągu z dwóch lub więcej istniejących obiektów. Zapewnia niezależny od języka sposób łączenia ciągów. Ta metoda akceptuje dowolną klasę, która pochodzi z **System.Object**. Poniższy przykład tworzy ciąg z dwóch istniejących obiektów ciągu i znak oddzielający.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **String.Join** Metoda tworzy nowy ciąg z tablicy ciągów i ciąg separatora. Ta metoda jest przydatna, jeśli chcesz połączyć wiele ciągów razem, dzięki czemu lista może być oddzielone przecinkiem.  
  
 W poniższym przykładzie użyto spacji do powiązania tablicy ciągów.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** Metoda tworzy nowy ciąg, wstawiając ciąg do określonej pozycji w innym ciągu. Ta metoda używa indeksu od zera. Poniższy przykład wstawia ciąg do piątej `MyString` pozycji indeksu i tworzy nowy ciąg z tą wartością.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>Copyto  
 Metoda **String.CopyTo** kopiuje fragmenty ciągu do tablicy znaków. Można określić zarówno indeks początkowy ciągu, jak i liczbę znaków do skopiowania. Ta metoda pobiera indeks źródłowy, tablicę znaków, indeks docelowy i liczbę znaków do skopiowania. Wszystkie indeksy są oparte na zeru.  
  
 W poniższym przykładzie użyto **CopyTo** metody skopiować znaki słowa "Hello" z obiektu ciągu do pierwszej pozycji indeksu tablicy znaków.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
