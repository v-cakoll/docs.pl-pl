---
title: Korzystanie z klasy StringBuilder w .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121675"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Korzystanie z klasy StringBuilder w .NET
Obiekt <xref:System.String> jest niezmienny. Za każdym razem, gdy używasz <xref:System.String?displayProperty=nameWithType> jednej z metod w klasie, należy utworzyć nowy obiekt ciągu w pamięci, który wymaga nowej alokacji miejsca dla tego nowego obiektu. W sytuacjach, w których należy wykonać powtarzające się modyfikacje ciągu, <xref:System.String> obciążenie związane z tworzeniem nowego obiektu może być kosztowne. Klasa <xref:System.Text.StringBuilder?displayProperty=nameWithType> może być używana, gdy chcesz zmodyfikować ciąg bez tworzenia nowego obiektu. Na przykład przy <xref:System.Text.StringBuilder> użyciu klasy można zwiększyć wydajność podczas łączenia wielu ciągów razem w pętli.  
  
## <a name="importing-the-systemtext-namespace"></a>Importowanie obszaru nazw System.Text  
 Klasa <xref:System.Text.StringBuilder> znajduje się <xref:System.Text> w obszarze nazw.  Aby uniknąć konieczności podawania w kodzie w pełni kwalifikowanej <xref:System.Text> nazwy typu, można zaimportować obszar nazw:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Tworzenie wystąpienia obiektu StringBuilder  
 Można utworzyć nowe wystąpienie <xref:System.Text.StringBuilder> klasy, inicjując zmienną za pomocą jednej z przeciążonych metod konstruktora, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Ustawianie pojemności i długości  
 Mimo <xref:System.Text.StringBuilder> że obiekt dynamiczny jest obiektem dynamicznym, który umożliwia rozszerzenie liczby znaków w ciągu, który zawiera, można określić wartość dla maksymalnej liczby znaków, które może pomieścić. Ta wartość jest wywoływana pojemność obiektu i nie należy mylić z <xref:System.Text.StringBuilder> długością ciągu, który posiada bieżący. Na przykład można utworzyć nowe wystąpienie <xref:System.Text.StringBuilder> klasy z ciągiem "Hello", który ma długość 5 i można określić, że obiekt ma maksymalną pojemność 25. Podczas modyfikowania <xref:System.Text.StringBuilder>, nie powoduje ponownego przyalokacji rozmiaru dla siebie, dopóki nie zostanie osiągnięty pojemność. W takim przypadku nowe miejsce jest przydzielane automatycznie, a pojemność jest podwojona. Można określić pojemność <xref:System.Text.StringBuilder> klasy przy użyciu jednego z przeciążonych konstruktorów. W poniższym przykładzie `myStringBuilder` określono, że obiekt można rozwinąć do maksymalnie 25 spacji.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ponadto można użyć właściwości odczytu/zapisu, <xref:System.Text.StringBuilder.Capacity%2A> aby ustawić maksymalną długość obiektu. W poniższym przykładzie użyto **Capacity** właściwość do zdefiniowania maksymalnej długości obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 Metoda <xref:System.Text.StringBuilder.EnsureCapacity%2A> może służyć do sprawdzania pojemności bieżącego **StringBuilder**. Jeśli pojemność jest większa niż przekazana wartość, nie jest wprowadzana żadna zmiana; Jeśli jednak pojemność jest mniejsza niż przekazana wartość, bieżąca pojemność zostanie zmieniona w celu dopasowania do przekazanej wartości.  
  
 Obiekt <xref:System.Text.StringBuilder.Length%2A> można również przeglądać lub ustawiać. Jeśli właściwość **Length** zostanie ustawiona na wartość większą niż Właściwość **Capacity,** właściwość **Capacity** zostanie automatycznie zmieniona na tę samą wartość, co właściwość **Length.** Ustawienie **Length** właściwość do wartości, która jest mniejsza niż długość ciągu w bieżącym **StringBuilder** skraca ciąg.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modyfikowanie ciągu StringBuilder  
 W poniższej tabeli wymieniono metody, których można użyć do zmodyfikowania zawartości **stringbuildera**.  
  
|Nazwa metody|Użycie|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Dołącza informacje na końcu bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Zastępuje specyfikator formatu przekazany w ciągu sformatowanym tekstem.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Wstawia ciąg lub obiekt do określonego indeksu bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Zastępuje określony znak w określonym indeksie.|  
  
### <a name="append"></a>Append  
 **Append** Metoda może służyć do dodawania tekstu lub reprezentacji ciągu obiektu na końcu ciągu reprezentowanego przez bieżące **StringBuilder**. Poniższy przykład inicjuje **StringBuilder** do "Hello World", a następnie dołącza tekst na końcu obiektu. W razie potrzeby miejsce jest przydzielane automatycznie.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>Format dodatku  
 Metoda <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> dodaje tekst na końcu <xref:System.Text.StringBuilder> obiektu. Obsługuje funkcję formatowania złożonego (aby uzyskać więcej informacji, zobacz <xref:System.IFormattable> [Formatowanie kompozytowe](../../../docs/standard/base-types/composite-formatting.md)), wywołując implementację obiektu lub obiektów, które mają zostać sformatowane. W związku z tym akceptuje standardowe ciągi formatu dla wartości liczbowych, daty i godziny oraz wyliczenia, niestandardowe ciągi formatu dla wartości liczbowych oraz daty i godziny oraz ciągi formatu zdefiniowane dla typów niestandardowych. (Aby uzyskać informacje o formatowaniu, zobacz [Typy formatowania](../../../docs/standard/base-types/formatting-types.md)). Tej metody można użyć do dostosowania formatu zmiennych i <xref:System.Text.StringBuilder>dosadowania tych wartości do pliku . W poniższym <xref:System.Text.StringBuilder.AppendFormat%2A> przykładzie użyto metody, aby umieścić wartość całkowitą sformatowaną jako wartość waluty na końcu <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 Metoda <xref:System.Text.StringBuilder.Insert%2A> dodaje ciąg lub obiekt do określonej pozycji <xref:System.Text.StringBuilder> w bieżącym obiekcie. W poniższym przykładzie użyto tej metody, aby <xref:System.Text.StringBuilder> wstawić wyraz do szóstej pozycji obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Remove  
 **Za** pomocą remove metody można usunąć określoną liczbę znaków <xref:System.Text.StringBuilder> z bieżącego obiektu, począwszy od określonego indeksu od zera. W poniższym **Remove** przykładzie użyto <xref:System.Text.StringBuilder> Remove metody, aby skrócić obiekt.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Replace  
 Metoda **Zamień** może służyć do <xref:System.Text.StringBuilder> zastępowania znaków w obiekcie innym określonym znakiem. W poniższym **Replace** przykładzie użyto <xref:System.Text.StringBuilder> Replace metody do wyszukiwania obiektu dla wszystkich wystąpień znaku wykrzyknika (!) i zastąpić je znakiem zapytania (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Konwertowanie obiektu StringBuilder na ciąg znaków  
 Należy przekonwertować <xref:System.Text.StringBuilder> obiekt <xref:System.String> na obiekt, zanim będzie można <xref:System.Text.StringBuilder> przekazać ciąg reprezentowany <xref:System.String> przez obiekt do metody, która ma parametr lub wyświetlić go w interfejsie użytkownika. Możesz wykonać tę konwersję, wywołując <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metodę. Poniższy przykład wywołuje szereg <xref:System.Text.StringBuilder> metod, a <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> następnie wywołuje metodę do wyświetlania ciągu.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>
- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
