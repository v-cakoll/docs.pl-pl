---
title: Dynamiczne ładowanie i używanie typów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- late binding, about late binding
- early binding
- dynamically loading and using types
- implicit late binding
- reflection, dynamically using types
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9795fa411d3b81f9092ddab183c6978ee701ef67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397978"
---
# <a name="dynamically-loading-and-using-types"></a>Dynamiczne ładowanie i używanie typów
Odbicie oferuje infrastrukturę, takie jak używany przez Kompilatory języka [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] i JScript do zaimplementowania ukryte późne powiązania. Powiązanie to proces lokalizowania deklaracji (wykonanie), która odpowiada jednoznacznie określonego typu. Ten proces odbywa się w czasie wykonywania, a nie w czasie kompilacji, jest nazywany późnego wiązania. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] Umożliwia użycie ukryte późne wiązania w kodzie; Kompilator Visual Basic wywołuje metodę pomocnika, która używa odbicia w celu uzyskania typu obiektu. Argumenty przekazane do metody pomocnika spowodować odpowiedniej metody do wywołania w czasie wykonywania. Te argumenty są wystąpienia (obiekt) do wywołania metody, nazwę wywoływanej metody (ciąg) i argumenty przekazane do wywołana metoda (Tablica obiektów).  
  
 W poniższym przykładzie kompilator Visual Basic używa odbicia niejawnie można wywołać metody dla obiekt, którego typ jest nieznany w czasie kompilacji. A **HelloWorld** klasa ma **PrintHello** do drukowania "Hello World" połączony z tekstem, który jest przekazywany do metody **PrintHello** metody. **PrintHello** metoda wywoływana w tym przykładzie jest rzeczywiście <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; kod Visual Basic umożliwia **PrintHello** metoda do wywołania, tak jakby były znany typ obiektu (helloObj), w kompilacji czas (wczesnego wiązania), a nie na wykonawczego (LCID).  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## <a name="custom-binding"></a>Powiązanie niestandardowe  
 Oprócz używana niejawnie przez kompilatory dla późne wiązanie, odbicia można jawnie w kodzie celu późnego wiązania.  
  
 [Środowisko uruchomieniowe języka wspólnego](../../../docs/standard/clr.md) obsługuje wiele języków programowania i powiązanie reguły z tych języków różnią się. W przypadku z wczesnym wiązaniem generatory kodu można całkowicie kontrolować tego powiązania. Jednak w późne wiązanie przez odbicie powiązanie muszą być kontrolowane przez powiązanie niestandardowe. <xref:System.Reflection.Binder> Klasa udostępnia formantu niestandardowego elementu członkowskiego, wybór i wywołania.  
  
 Przy użyciu niestandardowego powiązania, można załadować zestawu w czasie wykonywania, uzyskaj informacje na temat typów, w tym zestawie, określ typ, który ma, a następnie wywołaj metod lub dostępu do pola lub właściwości tego typu. Ta metoda jest przydatna, jeśli nie znasz typu obiektu w czasie kompilacji, na przykład, gdy typ obiektu jest zależny od danych wejściowych użytkownika.  
  
 W poniższym przykładzie pokazano integratora niestandardowych proste zapewnia brak konwersji typu argumentu. Kod `Simple_Type.dll` poprzedza Najlepszym przykładem. Pamiętaj utworzyć `Simple_Type.dll` , a następnie dołącz odwołanie do niej w projekcie w czasie kompilacji.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>Element InvokeMember i CreateInstance  
 Użyj <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> można wywołać elementu członkowskiego typu. **CreateInstance** klasy różnych metod, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> i <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, są specjalne rodzaje **Element InvokeMember** aby tworzenia nowych wystąpień określonego typu. **Integratora** klasa jest używana do przeciążenia rozdzielczość i argument koercja w tych metod.  
  
 W poniższym przykładzie przedstawiono trzy możliwe kombinacje koercja argumentu (konwersji typów) i wyboru elementu członkowskiego. W przypadku 1 niezbędne jest Brak argumentu zaznaczenia koercja lub elementu członkowskiego. W przypadku 2 wymagane jest tylko wyboru elementu członkowskiego. W przypadku 3 wymagany jest tylko koercja argumentu.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Rozpoznanie przeciążenia jest potrzebna, jeśli jest dostępny więcej niż jeden element członkowski o takiej samej nazwie. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> i <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> metody są używane do rozpoznawania powiązanie do jednego elementu członkowskiego. **Binder.BindToMethod** udostępnia rozpoznawanie właściwości za pomocą **uzyskać** i **ustawić** metod dostępu do właściwości.  
  
 **BindToMethod** zwraca <xref:System.Reflection.MethodBase> do wywołania, lub odwołanie o wartości null (**nic** w języku Visual Basic) Jeśli nie ma takich wywołania jest możliwe. **MethodBase** zwrócić wartość nie powinna być jedna z tych zawartych w *odpowiada* parametru, ale jest zwykle case.  
  
 Jeśli podano argumenty ByRef wywołujący może być ich odzyskania. W związku z tym **integratora** umożliwia klientowi mapy tablica argumentów do postaci oryginalnej, jeśli **BindToMethod** ma manipulować tablica argumentów. Aby to zrobić, należy zagwarantować wywołującego niezmieniona Kolejność argumentów. Gdy argumenty są przekazywane według nazw, **integratora** zmienia kolejność tablica argumentów, i który jest widzi wywołującego. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Zestaw dostępnych elementów członkowskich są takie elementy zdefiniowane w typie lub dowolnego typu podstawowego. Jeśli <xref:System.Reflection.BindingFlags> określono członkami żadnych ułatwień dostępu, które zostaną zwrócone w zestawie. Jeśli **flagę BindingFlags.NonPublic** nie zostanie określona, obiekt wiążący muszą wymuszać zasady ułatwień dostępu. Podczas określania **publicznego** lub **NonPublic** Flaga powiązanie, należy także określić **wystąpienia** lub **statycznych** powiązanie flagi lub nie elementy członkowskie zostaną zwrócone.  
  
 Jeśli istnieje tylko jeden element członkowski o podanej nazwie, niezbędne jest bez wywołania zwrotnego i powiązania jest wykonywana na tej metody. Przypadek 1 Przykładowy kod przedstawia tego punktu: tylko jeden **PrintBob** metoda jest dostępna, i dlatego trzeba bez wywołania zwrotnego.  
  
 Jeśli istnieje więcej niż jeden element członkowski w zestawie dostępności, wszystkie te metody są przekazywane do **BindToMethod**, który wybiera odpowiednią metodę i zwraca go. W przypadku 2 przykładów kodu, istnieją dwie metody o nazwie **PrintValue**. Wybrano odpowiednią metodę przez wywołanie **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> wykonuje koercja argumentu (konwersji typów), który konwertuje rzeczywistych argumentów typu Argumenty formalne wybranej metody. **ChangeType** jest wywoływana dla każdego argumentu, nawet wtedy, gdy typy są takie same.  
  
 W przypadku 3 przykładów kodu, rzeczywisty argument typu **ciąg** o wartości "5.5" jest przekazywany do metody z formalnego argumentu typu **podwójne**. Wywołania do pomyślnego wartość ciągu "5.5" musi można przekonwertować na wartość podwójną. **ChangeType** wykonuje konwersji.  
  
 **ChangeType** tylko przeprowadza bezstratne lub [rozszerzanie wymuszeniami](../../../docs/standard/base-types/type-conversion.md), jak pokazano w poniższej tabeli.  
  
|Typ źródła|Typ docelowy|  
|-----------------|-----------------|  
|Dowolnego typu|Jego typ podstawowy|  
|Dowolnego typu|Interfejs ją implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, Single, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, jeden dwukrotnie|  
|UInt64|Single, Double|  
|Int64|Single, Double|  
|Single|Double|  
|Typ nieinformacyjne|Typ odwołania|  
  
 <xref:System.Type> Klasa ma **uzyskać** metody, które używają parametrów typu **integratora** do rozpoznawania odwołań do określonego elementu członkowskiego. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, i <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> wyszukiwanie określonego składnika bieżącego typu, podając informacje o podpisie dla tego elementu członkowskiego. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> i <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> są wywołanie zwrotne do wybierz informacje o danym podpisem odpowiednich metod.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>  
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>  
 [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Konwersja typów w programie .NET Framework](../../../docs/standard/base-types/type-conversion.md)
