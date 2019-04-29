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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94ac21dfdf58e8aa1b629604792ad2f0f57c60d4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650417"
---
# <a name="creating-new-strings-in-net"></a>Tworzenie nowych ciągów w programie .NET
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umożliwia ciągów, które ma zostać utworzony przy użyciu przypisanie proste, a także przeciążenia konstruktora klasy obsługuje tworzenie ciągów za pomocą kilku różnych parametrów. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Również udostępnia kilka metod w <xref:System.String?displayProperty=nameWithType> klasy, które tworzyć nowe parametry obiekty, łącząc kilka ciągów, tablic ciągów, lub obiektów.  
  
## <a name="creating-strings-using-assignment"></a>Tworzenie ciągów za pomocą przypisania  
 Najprostszym sposobem utworzenia nowego <xref:System.String> obiektu jest po prostu przypisać literału ciągu na <xref:System.String> obiektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Tworzenie ciągów za pomocą konstruktora klasy  
 Możesz użyć przeciążenia <xref:System.String> konstruktora klasy, aby utworzyć ciągów na podstawie tablic znaków. Można również utworzyć nowy ciąg, duplikując określonego znaku określoną liczbę razy.  
  
## <a name="methods-that-return-strings"></a>Metody, które zwracają ciągów  
 W poniższej tabeli wymieniono kilka użytecznych metod, które zwracają nowe obiekty ciągów.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Tworzy ciąg formatowania z zestawu danych wejściowych obiektów.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Tworzy ciągi z co najmniej dwóch ciągów.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Tworzy nowy ciąg, łącząc tablicę ciągów.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Tworzy nowy ciąg wstawiając ciąg do określonego indeksu istniejącego ciągu.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Kopiuje określone znaków w ciągu w określonej pozycji w tablicy znaków.|  
  
### <a name="format"></a>Format  
 Możesz użyć **String.Format** metodę, aby utworzyć sformatowane ciągi i łączenie ciągów reprezentujących wielu obiektów. Ta metoda automatycznie konwertuje każdy przekazany obiekt na ciąg. Na przykład, jeśli aplikacja musi wyświetlić **Int32** wartość i **daty/godziny** wartość dla użytkownika, można łatwo utworzyć ciąg reprezentujący te wartości przy użyciu **Format**metody. Informacje na temat formatowania Konwencji używanych przy użyciu tej metody, zobacz sekcję na [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md).  
  
 W poniższym przykładzie użyto **Format** metodę, aby utworzyć ciąg, który używa zmiennej liczby całkowitej.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 W tym przykładzie<xref:System.DateTime.Now%2A?displayProperty=nameWithType> Wyświetla bieżącą datę i godzinę w sposób określony przez kultury skojarzonej z bieżącym wątkiem.  
  
### <a name="concat"></a>concat  
 **String.concat —** metody można łatwo utworzyć nowy obiekt ciągu z co najmniej dwóch istniejących obiektów. Umożliwia łączenie ciągów w sposób niezależny od języka. Ta metoda przyjmuje dowolną klasę pochodzącą od **System.Object**. Poniższy przykład tworzy ciąg z dwóch istniejących obiektów ciągu i znak oddzielający.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Łączenie  
 **String.Join** metoda tworzy nowy ciąg z tablicy ciągów i ciągu separatora. Ta metoda jest przydatna, jeśli chcesz łączyć wiele ciągi, tworzenie listy może być rozdzielone przecinkami.  
  
 W poniższym przykładzie użyto spację, aby powiązać tablicy ciągów.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** metoda tworzy nowy ciąg wstawiając ciąg do określonej pozycji w innym ciągu. Ta metoda korzysta z indeksu. Poniższy przykład wstawia ciąg do piątego pozycja indeksu parametru `MyString` i tworzy nowy ciąg o tej wartości.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** metoda kopiuje części ciągu do tablicy znaków. Można określić indeksu początku ciągu i liczba znaków do skopiowania. Ta metoda przyjmuje indeks źródła, tablicę znaków, indeksu docelowego i liczba znaków do skopiowania. Wszystkie indeksy są oparte na zerze.  
  
 W poniższym przykładzie użyto **CopyTo** metodę, aby skopiować znaki wyraz "Hello" z ciągu obiektu do pierwszej pozycji indeksu tablicy znaków.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)
