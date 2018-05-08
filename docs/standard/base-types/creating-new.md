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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9f0c487d3d04af998fb1c3339d736e9bb043374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-new-strings-in-net"></a>Tworzenie nowych ciągów w .NET
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umożliwia ciągów, które ma zostać utworzony przy użyciu przypisanie proste, a także overloads konstruktora klasy do obsługi tworzenia ciągu przy użyciu wielu różnych parametrów. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia kilka metod w <xref:System.String?displayProperty=nameWithType> klasy, która utworzyć nowe parametry obiektów przez łączenie wielu ciągów, tablic ciągów, ani obiektów.  
  
## <a name="creating-strings-using-assignment"></a>Tworzenie ciągów za pomocą przypisania  
 Najprostszym sposobem, aby utworzyć nową <xref:System.String> obiektu jest po prostu przypisanie literału ciągu na <xref:System.String> obiektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Tworzenie ciągów za pomocą konstruktora klasy  
 Można użyć przeciążeń <xref:System.String> konstruktora klasy w celu utworzenia ciągów w tablice znaków. Można również utworzyć nowe parametry, duplikując określonego znaku określoną liczbę razy.  
  
## <a name="methods-that-return-strings"></a>Metody zwracające ciągów  
 W poniższej tabeli wymieniono kilka metod przydatne, które zwracają nowe obiekty ciągu.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Tworzy ciąg sformatowany za pomocą zestawu wejściowego obiektów.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Tworzy ciągów z co najmniej dwa parametry.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Tworzy nowe parametry, łącząc tablicy ciągów.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Tworzy nowe parametry wstawiając ciąg do określonego indeksu istniejące parametry.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Kopiuje określone znaków w ciągu w określonej pozycji w tablicy znaków.|  
  
### <a name="format"></a>Format  
 Można użyć **String.Format** metody do tworzenia ciągi sformatowane i łączenie ciągów reprezentujących wielu obiektów. Ta metoda powoduje automatyczną konwersję dowolnego przekazanego obiektu na ciąg. Na przykład, jeśli aplikacja musi zawierać **Int32** wartość i **DateTime** wartość dla użytkownika, można łatwo utworzyć ciąg do reprezentowania te wartości przy użyciu **Format**metody. Informacje na temat formatowania konwencje używane z tą metodą, zobacz sekcję dotyczącą [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md).  
  
 W poniższym przykładzie użyto **Format** metodę w celu utworzenia ciąg, który używa zmienna typu Liczba całkowita.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 W tym przykładzie<xref:System.DateTime.Now%2A?displayProperty=nameWithType> Wyświetla bieżącą datę i godzinę w sposób określony przez kultury skojarzone z bieżącego wątku.  
  
### <a name="concat"></a>concat  
 **String.concat —** — metoda pozwala łatwo utworzyć nowy obiekt ciągu z dwóch lub więcej istniejących obiektów. Zapewnia sposób niezależny od języka aby ciągów. Ta metoda przyjmuje dowolnej klasy, która jest pochodną **System.Object**. Poniższy przykład tworzy ciąg z dwóch istniejących obiektów ciągu i znak oddzielający.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Łączenie  
 **String.Join** metoda tworzy nowego ciągu z tablicy ciągów i ciąg separatora. Ta metoda jest przydatna, jeśli chcesz łączenie wielu ciągów, tworzenie listy prawdopodobnie rozdzielonych przecinkami.  
  
 W poniższym przykładzie użyto spację, aby powiązać tablicy ciągów.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** metoda tworzy nowy ciąg wstawiając ciąg do określonej pozycji w innym ciągu. Ta metoda korzysta z indeksu. Poniższy przykład wstawia ciąg do piątego indeks `MyString` i tworzy nowy ciąg o tej wartości.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>Wykonanie operacji kopiowania  
 **String.CopyTo** metody kopiuje części ciągu do tablicy znaków. Można określić indeksu początku ciąg i liczbę znaków do skopiowania. Ta metoda przyjmuje indeks źródła, tablicy znaków indeksu docelowego i liczbę znaków do skopiowania. Wszystkie indeksy są liczony od zera.  
  
 W poniższym przykładzie użyto **CopyTo** metodę, aby skopiować znaki Word tekst "Hello" z ciągu obiektu na pierwszym miejscu indeksu tablicy znaków.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
 [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
