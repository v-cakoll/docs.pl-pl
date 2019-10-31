---
title: Korzystanie z klasy StringBuilder w środowisku .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
ms.openlocfilehash: 19ee90f3300e3b610eeefd4949baa2759b834a60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121675"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Korzystanie z klasy StringBuilder w środowisku .NET
Obiekt <xref:System.String> jest niezmienny. Za każdym razem, gdy używasz jednej z metod w klasie <xref:System.String?displayProperty=nameWithType>, utworzysz nowy obiekt String w pamięci, co wymaga nowego przydziału miejsca dla nowego obiektu. W sytuacjach, gdy trzeba wykonać powtórzone modyfikacje ciągu, obciążenie związane z tworzeniem nowego obiektu <xref:System.String> może być kosztowne. Klasy <xref:System.Text.StringBuilder?displayProperty=nameWithType> można użyć, jeśli chcesz zmodyfikować ciąg bez tworzenia nowego obiektu. Na przykład użycie klasy <xref:System.Text.StringBuilder> może zwiększyć wydajność podczas łączenia wielu ciągów razem w pętli.  
  
## <a name="importing-the-systemtext-namespace"></a>Importowanie przestrzeni nazw System. Text  
 Klasa <xref:System.Text.StringBuilder> znajduje się w przestrzeni nazw <xref:System.Text>.  Aby uniknąć konieczności podawania w kodzie w pełni kwalifikowanej nazwy typu, możesz zaimportować <xref:System.Text> przestrzeni nazw:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Tworzenie wystąpienia obiektu StringBuilder  
 Można utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder>, inicjując zmienną za pomocą jednej z przeciążonych metod konstruktora, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Ustawianie pojemności i długości  
 Chociaż <xref:System.Text.StringBuilder> jest obiektem dynamicznym, który pozwala rozwijać liczbę znaków w ciągu, który jest hermetyzowany, można określić wartość maksymalnej dozwolonej liczby znaków. Ta wartość jest określana jako pojemność obiektu i nie należy jej mylić z długością ciągu, w którym znajduje się bieżąca <xref:System.Text.StringBuilder>. Można na przykład utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder> z ciągiem "Hello", który ma długość 5 i można określić, że obiekt ma maksymalną pojemność wynoszącą 25. Modyfikacja <xref:System.Text.StringBuilder>nie powoduje ponownego przydzielania rozmiaru dla siebie, dopóki nie zostanie osiągnięta pojemność. W takim przypadku nowe miejsce zostanie przydzieloną automatycznie, a pojemność jest podwójna. Możesz określić pojemność klasy <xref:System.Text.StringBuilder> przy użyciu jednego z przeciążonych konstruktorów. Poniższy przykład określa, że obiekt `myStringBuilder` może być rozszerzony do maksymalnie 25 spacji.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ponadto można użyć właściwości <xref:System.Text.StringBuilder.Capacity%2A> do odczytu/zapisu, aby ustawić maksymalną długość obiektu. W poniższym przykładzie użyta jest właściwość **pojemności** do zdefiniowania maksymalnej długości obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Metoda <xref:System.Text.StringBuilder.EnsureCapacity%2A> może służyć do sprawdzenia pojemności bieżącego elementu **StringBuilder**. Jeśli pojemność jest większa niż wartość przeniesiona, nie wprowadzono żadnych zmian. Jeśli jednak pojemność jest mniejsza niż wartość przeniesiona, bieżąca pojemność jest zmieniana, aby odpowiadała wartości z przekazaną.  
  
 Właściwość <xref:System.Text.StringBuilder.Length%2A> może być również wyświetlana lub ustawiona. Jeśli właściwość **Length** zostanie ustawiona na wartość większą niż Właściwość **pojemności** , właściwość **pojemności** zostanie automatycznie zmieniona na taką samą wartość jak Właściwość **Length** . Ustawienie właściwości **Length** na wartość, która jest mniejsza niż długość ciągu w bieżącym **StringBuilder** , skraca ciąg.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modyfikowanie ciągu StringBuilder  
 Poniższa tabela zawiera listę metod, których można użyć w celu zmodyfikowania zawartości **StringBuilder**.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Dołącza informacje na końcu bieżącego elementu **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Zastępuje specyfikator formatu przekazaną w ciągu sformatowanym tekstem.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Wstawia ciąg lub obiekt do określonego indeksu bieżącego elementu **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z bieżącego elementu **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Zastępuje określony znak w określonym indeksie.|  
  
### <a name="append"></a>łączono  
 Metoda **append** może służyć do dodawania tekstu lub reprezentowania ciągu obiektu na końcu ciągu reprezentowanego przez bieżący element **StringBuilder**. Poniższy przykład Inicjuje element **StringBuilder** do "Hello World", a następnie dołącza jakiś tekst na końcu obiektu. Miejsce jest przypisywany automatycznie, zgodnie z wymaganiami.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 Metoda <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> dodaje tekst na końcu obiektu <xref:System.Text.StringBuilder>. Obsługuje funkcję formatowania złożonego (Aby uzyskać więcej informacji, zobacz [formatowanie złożone](../../../docs/standard/base-types/composite-formatting.md)) przez wywołanie <xref:System.IFormattable> implementacji obiektu lub obiektów do sformatowania. W związku z tym akceptuje ciągi formatu standardowego dla wartości liczbowych, daty i godziny oraz wyliczenia, niestandardowych ciągów formatu dla wartości liczbowych i daty i godziny oraz ciągów formatu zdefiniowanych dla typów niestandardowych. (Aby uzyskać informacje na temat formatowania, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md)). Tej metody można użyć do dostosowania formatu zmiennych i dołączenia tych wartości do <xref:System.Text.StringBuilder>. W poniższym przykładzie zastosowano metodę <xref:System.Text.StringBuilder.AppendFormat%2A>, aby umieścić wartość całkowitą sformatowaną jako wartość walutową na końcu obiektu <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 Metoda <xref:System.Text.StringBuilder.Insert%2A> dodaje ciąg lub obiekt do określonej pozycji w bieżącym obiekcie <xref:System.Text.StringBuilder>. Poniższy przykład używa tej metody do wstawienia wyrazu do szóstego położenia obiektu <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Usuń  
 Możesz użyć metody **Remove** , aby usunąć określoną liczbę znaków z bieżącego obiektu <xref:System.Text.StringBuilder>, zaczynając od określonego indeksu na podstawie zera. Poniższy przykład używa metody **Remove** do skracania obiektu <xref:System.Text.StringBuilder>.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>stępować  
 Metoda **replace** może służyć do zastępowania znaków w obiekcie <xref:System.Text.StringBuilder> innym określonym znakiem. W poniższym przykładzie zastosowano metodę **replace** , aby przeszukać <xref:System.Text.StringBuilder> obiektu dla wszystkich wystąpień znaku wykrzyknika (!) i zastąpić je znakiem znaku zapytania (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Konwertowanie obiektu StringBuilder na ciąg  
 Przed przekazaniem ciągu reprezentowanego przez obiekt <xref:System.Text.StringBuilder> do metody, która ma parametr <xref:System.String> lub wyświetlenie w interfejsie użytkownika, należy przekonwertować obiekt <xref:System.Text.StringBuilder> na obiekt <xref:System.String>. Tę konwersję można wykonać, wywołując metodę <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>. Poniższy przykład wywołuje wiele metod <xref:System.Text.StringBuilder>, a następnie wywołuje metodę <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType>, aby wyświetlić ciąg.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
