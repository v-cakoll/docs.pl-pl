---
title: Używanie klasy StringBuilder w .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6db9d2e1e075b9908e4c6db3d327f446980e98a5
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2018
ms.locfileid: "37072959"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Używanie klasy StringBuilder w .NET
<xref:System.String> Obiektu nie można modyfikować. Zawsze używać jednej z metod w <xref:System.String?displayProperty=nameWithType> klasy, należy utworzyć nowy obiekt ciąg w pamięci, co wymaga nowej przydzielenie miejsca dla nowego obiektu. W sytuacjach, w którym należy przeprowadzić modyfikacji powtarzane na ciąg, obciążenie skojarzone z tworzeniem nowego <xref:System.String> obiekt może być kosztowne. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Klasa może być używana, gdy chcesz zmodyfikować ciąg bez tworzenia nowego obiektu. Na przykład za pomocą <xref:System.Text.StringBuilder> klasy może zwiększyć wydajność, gdy łączenie wielu ciągów w pętli.  
  
## <a name="importing-the-systemtext-namespace"></a>Importowanie Namespace System.Text  
 <xref:System.Text.StringBuilder> Klasa znajduje się w <xref:System.Text> przestrzeni nazw.  Aby uniknąć konieczności podawania w pełni kwalifikowana nazwa typu w kodzie, można importować <xref:System.Text> przestrzeni nazw:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Utworzenie wystąpienia obiektu klasy StringBuilder  
 Można utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder> klasy przez inicjowanie zmiennej użytkownika przy użyciu jednej z metod przeciążonego konstruktora, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Ustawienia pojemności i długość  
 Mimo że <xref:System.Text.StringBuilder> jest to obiekt dynamiczny, która pozwala na liczbę znaków w ciągu, który hermetyzuje, rozwiń można określić wartości maksymalnej liczby znaków, które może on zawierać. Ta wartość jest nazywana pojemności obiektu i nie należy mylić z długość ciągu który bieżącego <xref:System.Text.StringBuilder> przechowuje. Na przykład można utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder> klasy z ciągiem "Hello", która ma długość 5, i może określić, że obiekt ma maksymalną pojemność 25. Po zmodyfikowaniu <xref:System.Text.StringBuilder>, nie alokację rozmiar dla siebie aż do osiągnięcia pojemność. W takim przypadku nowe miejsce jest przydzielane automatycznie i pojemność jest podwójny. Należy określić pojemność <xref:System.Text.StringBuilder> przy użyciu jednego z konstruktorów przeciążona. Poniższy przykład określa, że `myStringBuilder` obiektu można rozszerzyć, aby maksymalnie 25 spacji.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ponadto można użyć odczytu/zapisu <xref:System.Text.StringBuilder.Capacity%2A> właściwości, aby ustawić maksymalną długość obiektu. W poniższym przykładzie użyto **pojemności** właściwości, aby określić maksymalną długość.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Metody można użyć do sprawdzenia zdolności bieżącego **StringBuilder**. Jeśli pojemność jest większa niż wartość przekazany, nie zostaną zmienione; Jeśli pojemność jest mniejsza niż wartość przekazany, pojemność bieżąca zostanie zmieniona na zgodną z wartością przekazany.  
  
 <xref:System.Text.StringBuilder.Length%2A> Również można wyświetlić lub ustawić właściwości. Jeśli ustawisz **długość** właściwości na wartość, która jest większa niż **pojemności** właściwość **pojemności** automatycznie jest zmieniana na taką samą wartość jak  **Długość** właściwości. Ustawienie **długość** właściwości na wartość, która jest mniejsza niż długość ciągu w bieżącej **StringBuilder** skraca ciąg.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modyfikowanie ciąg StringBuilder  
 W poniższej tabeli przedstawiono metody służy do modyfikowania zawartości **StringBuilder**.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Dołącza informacji do końca bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Zastępuje specyfikator formatu przekazany ciąg znaków z tekstu sformatowanego.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Wstawia ciąg lub obiekt w określonym indeksie bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Zamienia określony znak pod określonym indeksem.|  
  
### <a name="append"></a>Dołącz  
 **Append** metody można użyć do dodawania tekstu lub reprezentację ciągu obiektu do końca ciągu reprezentowany przez bieżące **StringBuilder**. W poniższym przykładzie inicjowane **StringBuilder** na "Hello World", a następnie dołącza tekst na końcu obiektu. Miejsce jest przydzielane w razie potrzeby automatycznie.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>AppendFormat  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Metoda dodaje tekst na końcu <xref:System.Text.StringBuilder> obiektu. Obsługuje funkcję formatowania złożonego (Aby uzyskać więcej informacji, zobacz [złożone formatowanie](../../../docs/standard/base-types/composite-formatting.md)) przez wywołanie metody <xref:System.IFormattable> implementacji obiektu lub obiektów do sformatowania. W związku z tym akceptuje standardowe ciągi formatujące wartości liczbowe, daty i godziny oraz wyliczenia, ciągi formatu niestandardowego dla numeryczne i wartości daty i godziny i ciągi formatujące zdefiniowany dla typów niestandardowych. (Aby uzyskać informacje na temat formatowania, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).) Ta metoda służy do dostosowywania format zmiennych i dodać tych wartości <xref:System.Text.StringBuilder>. W poniższym przykładzie użyto <xref:System.Text.StringBuilder.AppendFormat%2A> metodę, aby umieścić wartość całkowitą sformatowane jako wartość walutową na końcu <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A> Metoda dodaje ciąg lub obiekt na określonej pozycji w bieżącym <xref:System.Text.StringBuilder> obiektu. W poniższym przykładzie użyto tej metody, aby wstawić wyraz do szóstego pozycja <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Usuń  
 Można użyć **Usuń** metodę, aby usunąć określoną liczbę znaków z bieżącego <xref:System.Text.StringBuilder> obiektu, rozpoczynając od określonego indeksu. W poniższym przykładzie użyto **Usuń** metody w celu skrócenia <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Zamień  
 **Zastąp** — metoda może być używany do zastąpienia znaków w <xref:System.Text.StringBuilder> określony obiekt z inną znak. W poniższym przykładzie użyto **Zastąp** metodę wyszukiwania <xref:System.Text.StringBuilder> obiekt wystąpienia wszystkich wykrzyknika (!) znaków i zastąpić je znak zapytania (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Konwertowanie obiektów StringBuilder do ciągu  
 Przekonwertuj <xref:System.Text.StringBuilder> do obiektu <xref:System.String> obiekt przed można przekazać reprezentowany przez ciąg <xref:System.Text.StringBuilder> obiektu do metody, która ma <xref:System.String> parametru lub wyświetlać go w interfejsie użytkownika. Wykonaj tę konwersję przez wywołanie metody <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metody. Poniższy przykład wywołuje szereg <xref:System.Text.StringBuilder> metod, a następnie wywołania <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> metodę, aby wyświetlić ciąg.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
 [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
 [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
