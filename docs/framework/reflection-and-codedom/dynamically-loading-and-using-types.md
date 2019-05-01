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
ms.openlocfilehash: 51e34d8eed40481de47dfd217392e95a11a412d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61983934"
---
# <a name="dynamically-loading-and-using-types"></a>Dynamiczne ładowanie i używanie typów
Odbicie zapewnia infrastrukturę, która używane przez Kompilatory języka, takich jak [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] i JScript w celu zaimplementowania ukryte późne powiązania. Powiązanie jest proces lokalizowania deklaracja (wykonanie), która odpowiada jednoznacznie określonym typie. Ten proces odbywa się w czasie wykonywania, a nie w czasie kompilacji, jest nazywany późnego wiązania. [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] pozwala na używanie ukryte późne powiązania w kodzie; Kompilator Visual Basic wywołuje metodę pomocnika, która używa odbicia w celu uzyskania typu obiektu. Argumenty przekazane do metody pomocnika spowodować odpowiedniej metody do wywołania w czasie wykonywania. Te argumenty są wystąpienie (obiekt) do wywołania metody, nazwę wywoływanej metody (ciąg), a argumenty przekazane do wywoływanej metody (tablicę obiektów).  
  
 W poniższym przykładzie kompilator Visual Basic używa odbicia niejawnie do wywołania metody na obiekt, którego typ nie jest znany w czasie kompilacji. A **HelloWorld** klasa ma **PrintHello** do drukowania "Hello World" połączona z tekstem, który jest przekazywany do metody **PrintHello** metody. **PrintHello** metodę o nazwie w tym przykładzie jest faktycznie <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; kodu języka Visual Basic umożliwia **PrintHello** metoda do wywołania, tak jakby były znane typ obiektu (helloObj), podczas kompilacji czas (wczesne powiązania), a nie na wykonawczego (LCID).  
  
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
  
## <a name="custom-binding"></a>Wiązanie niestandardowe  
 Oprócz używane niejawnie przez kompilatory dla późne powiązania, odbicie można jawnie w kodzie do wykonywania późnego wiązania.  
  
 [Środowiska uruchomieniowego języka wspólnego](../../../docs/standard/clr.md) obsługuje wiele języków programowania i powiązanie reguły z tych języków różnią się. W przypadku wczesnym wiązaniem generatorów kodu całkowicie można kontrolować to wiązanie. Jednak w późnym wiązaniem przy użyciu odbicia, powiązanie muszą być kontrolowane przez niestandardowe powiązanie. <xref:System.Reflection.Binder> Klasa udostępnia formantu niestandardowego elementu członkowskiego, wybór i wywołania.  
  
 Za pomocą niestandardowego powiązania, można załadować zestawu w czasie wykonywania, uzyskiwania informacji na temat typów, w tym zestawie, określić typ, który chcesz, a następnie wywołaj metodę lub dostęp do pól lub właściwości tego typu. Ta technika jest przydatna, jeśli typ obiektu nie jest znany w czasie kompilacji, na przykład, gdy typ obiektu jest zależny od danych wejściowych użytkownika.  
  
 W poniższym przykładzie pokazano prosty niestandardowego integratora, który zapewnia bez konwersji typu argumentu. Kod `Simple_Type.dll` poprzedza główny przykład. Pamiętaj tworzyć `Simple_Type.dll` , a następnie dołącz odwołanie do niej w projekcie w czasie kompilacji.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>Element InvokeMember i CreateInstance —  
 Użyj <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> można zainicjować członka typu. **CreateInstance —** klasy różnych metod, takich jak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> i <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, są specjalne rodzaje **Element InvokeMember** , tworzenie nowych wystąpień określonego typu. **Integratora** klasa jest używana do rozpoznawania i argument wymuszenia przeciążenia w tych metodach.  
  
 Poniższy przykład przedstawia trzy możliwe kombinacje wymuszenia argumentu (konwersji typów) i wybór elementów członkowskich. W przypadku 1 Brak zaznaczenia wymuszenia lub elementu członkowskiego, argument jest wymagany. W przypadku 2 jest wymagany tylko wybranych elementów członkowskich. W przypadku 3 tylko wymuszenia argument jest wymagany.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Rozpoznanie przeciążenia jest pożądane, gdy dostępnych jest więcej niż jeden element członkowski o takiej samej nazwie. <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> i <xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> metody są używane można rozpoznać powiązania do jednego elementu członkowskiego. **Binder.BindToMethod** udostępnia również właściwość rozwiązania za pośrednictwem **uzyskać** i **ustaw** metod dostępu do właściwości.  
  
 **BindToMethod** zwraca <xref:System.Reflection.MethodBase> do wywołania, lub odwołanie o wartości null (**nic** w języku Visual Basic) Jeśli nie takie wywołanie jest możliwe. **MethodBase** zwracają wartość nie musi być jednym z tych znajdujących się w *dopasowania* parametru, mimo że zwykle tak jest.  
  
 Gdy występują argumenty ByRef, obiekt wywołujący może być ich odzyskania. W związku z tym **integratora** umożliwia klientowi zamapować tablica argumentów do ich oryginalnej formie, jeśli **BindToMethod** ma manipulować tablica argumentów. Aby to zrobić, można zagwarantować obiekt wywołujący ulega Kolejność argumentów. Jeśli argumenty są przekazywane według nazwy, **integratora** zmienia kolejność tablica argumentów, a to znaczy obiekt wywołujący widzi. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Zestaw elementów członkowskich dostępne są te elementy członkowskie zdefiniowane w typie lub dowolnego typu podstawowego. Jeśli <xref:System.Reflection.BindingFlags> jest określony, elementy członkowskie z dowolnym opcjami dostępu, które zostaną zwrócone w zestawie. Jeśli **BindingFlags.NonPublic** nie zostanie określony, obiekt wiążący muszą wymuszać reguły ułatwień dostępu. Podczas określania **publicznych** lub **NonPublic** Flaga powiązania, należy także określić **wystąpienia** lub **statyczne** powiązanie flag lub nie elementy członkowskie zostaną zwrócone.  
  
 Jeśli istnieje tylko jeden element członkowski o podanej nazwie nie wywołanie zwrotne nie jest to konieczne, i powiązania odbywa się z tej metody. Przypadek 1 przykład kodu ilustruje tę sytuację: Tylko jeden **PrintBob** metoda jest dostępna i dlatego trzeba bez wywołania zwrotnego.  
  
 Jeśli istnieje więcej niż jeden element członkowski w zestawie dostępności, wszystkie te metody są przekazywane do **BindToMethod**, który wybiera odpowiednią metodę i zwraca go. W przypadku 2 przykładowy kod, istnieją dwie metody o nazwie **PrintValue**. Wybrano odpowiednią metodę przez wywołanie **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A> wykonuje wymuszenia argumentu (konwersji typów), która konwertuje rzeczywiste argumenty typu argumentów formalnych wybranej metody. **ChangeType** jest wywoływana dla każdego argumentu, nawet jeśli dokładnie takie same typy.  
  
 W przypadku 3 w przykładzie kodu, rzeczywisty argument typu **ciąg** z wartością "5.5" jest przekazywany do metody z formalnego argumentu typu **Double**. Wywołania zakończyło się sukcesem w na wartość podwójną musi przekonwertować daną wartość ciągu "5.5". **ChangeType** wykonuje tę konwersję.  
  
 **ChangeType** tylko przeprowadza bezstratne lub [rozszerzanie coercions](../../../docs/standard/base-types/type-conversion.md), jak pokazano w poniższej tabeli.  
  
|Typ źródła|Typ docelowy|  
|-----------------|-----------------|  
|Dowolnego typu|Jego typ podstawowy|  
|Dowolnego typu|Interfejs go implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, pojedynczy Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, pojedynczy Double|  
|SByte|Int16, Int32, Int64, pojedynczy Double|  
|UInt16|UInt32, Int32, UInt64, Int64, pojedynczy Double|  
|Int16|Int32, Int64, pojedynczy Double|  
|UInt32|UInt64, Int64, pojedynczy Double|  
|Int32|Int64, jeden dwukrotnie|  
|UInt64|Pojedynczy Double|  
|Int64|Pojedynczy Double|  
|Single|Double|  
|Typ nieinformacyjne|Typ odwołania|  
  
 <xref:System.Type> Klasa ma **uzyskać** metody, które używają parametrów typu **integratora** do rozpoznawania odwołań do określonego elementu członkowskiego. <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType>, i <xref:System.Type.GetProperty%2A?displayProperty=nameWithType> wyszukiwanie określonego elementu członkowskiego bieżącego typu poprzez dostarczanie informacji podpis dla tego elementu członkowskiego. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType> i <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> to wywołanie zwrotne do wybierz informacje o podpisie danego odpowiednich metod.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Konwersja typów w programie .NET Framework](../../../docs/standard/base-types/type-conversion.md)
