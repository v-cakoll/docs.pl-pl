---
title: Tworzenie nowych ciągów w programie .NET
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103819"
---
# <a name="creating-new-strings-in-net"></a>Tworzenie nowych ciągów w programie .NET
.NET Framework umożliwia tworzenie ciągów przy użyciu prostego przypisywania, a także przeciążenie konstruktora klasy do obsługi tworzenia ciągów przy użyciu wielu różnych parametrów. .NET Framework udostępnia również kilka metod w klasie <xref:System.String?displayProperty=nameWithType>, które tworzą nowe obiekty ciągu przez połączenie kilku ciągów, tablic ciągów lub obiektów.  
  
## <a name="creating-strings-using-assignment"></a>Tworzenie ciągów przy użyciu przypisania  
 Najprostszym sposobem utworzenia nowego obiektu <xref:System.String> jest przypisanie literału ciągu do <xref:System.String> obiektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Tworzenie ciągów przy użyciu konstruktora klasy  
 Można użyć overloads konstruktora klasy <xref:System.String> do tworzenia ciągów z tablic znaków. Możesz również utworzyć nowy ciąg, duplikując określony znak określoną liczbę razy.  
  
## <a name="methods-that-return-strings"></a>Metody, które zwracają ciągi  
 Poniższa tabela zawiera kilka przydatnych metod, które zwracają nowe obiekty ciągu.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Kompiluje sformatowany ciąg z zestawu obiektów wejściowych.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Kompiluje ciągi z dwóch lub więcej ciągów.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Kompiluje nowy ciąg, łącząc tablicę ciągów.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Kompiluje nowy ciąg przez wstawienie ciągu do określonego indeksu istniejącego ciągu.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Kopiuje określone znaki w ciągu do określonej pozycji w tablicy znaków.|  
  
### <a name="format"></a>Format  
 Za pomocą metody **String. format** można tworzyć sformatowane ciągi i łączyć ciągi reprezentujące wiele obiektów. Ta metoda automatycznie konwertuje każdy zakończony obiekt na ciąg. Na przykład, jeśli w aplikacji musi być wyświetlana wartość **Int32** i wartość **DateTime** dla użytkownika, można łatwo skonstruować ciąg do reprezentowania tych wartości przy użyciu metody **Format** . Aby uzyskać informacje na temat Konwencji formatowania używanych z tą metodą, zobacz sekcję dotyczącą [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).  
  
 W poniższym przykładzie zastosowano metodę **Format** , aby utworzyć ciąg, który używa zmiennej typu Integer.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 W tym przykładzie<xref:System.DateTime.Now%2A?displayProperty=nameWithType> wyświetla bieżącą datę i godzinę w sposób określony przez kulturę skojarzoną z bieżącym wątkiem.  
  
### <a name="concat"></a>Concat  
 Metoda **String. Concat** może służyć do łatwego tworzenia nowego obiektu ciągu z dwóch lub więcej istniejących obiektów. Zapewnia on niezależny od języka sposób łączenia ciągów. Ta metoda akceptuje wszelkie klasy, które pochodzą z **obiektu System. Object**. Poniższy przykład tworzy ciąg z dwóch istniejących obiektów String i oddzielający znak.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Łączenie  
 Metoda **String. Join** tworzy nowy ciąg z tablicy ciągów i ciągu separatora. Ta metoda jest przydatna, jeśli chcesz połączyć wiele ciągów ze sobą, tworząc listę, która może być oddzielona przecinkami.  
  
 Poniższy przykład używa spacji, aby powiązać tablicę ciągów.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 Metoda **String. Insert** tworzy nowy ciąg przez wstawienie ciągu do określonej pozycji w innym ciągu. Ta metoda używa indeksu na podstawie zera. Poniższy przykład wstawia ciąg do piątej pozycji indeksu `MyString` i tworzy nowy ciąg z tą wartością.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 Metoda **String. CopyTo** kopiuje fragmenty ciągu do tablicy znaków. Można określić zarówno początkowy indeks ciągu, jak i liczbę znaków, które mają zostać skopiowane. Ta metoda przyjmuje indeks źródłowy, tablicę znaków, indeks docelowy oraz liczbę znaków do skopiowania. Wszystkie indeksy są zależne od zera.  
  
 W poniższym przykładzie zastosowano metodę **CopyTo** , aby skopiować znaki wyrazu "Hello" z obiektu String do pierwszej pozycji indeksu tablicy znaków.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
