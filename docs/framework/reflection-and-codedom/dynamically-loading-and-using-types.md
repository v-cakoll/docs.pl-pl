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
ms.openlocfilehash: 0246f429b396a2606bbb827b7ae2a9034af00f11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915476"
---
# <a name="dynamically-loading-and-using-types"></a>Dynamiczne ładowanie i używanie typów
Odbicie zapewnia infrastrukturę używaną przez kompilatory języka do implementowania niejawnego późnego wiązania. Powiązanie jest procesem lokalizowania deklaracji (czyli implementacji), która odnosi się do jednoznacznie określonego typu. Gdy ten proces wystąpi w czasie wykonywania, a nie w czasie kompilacji, jest nazywany późnym wiązaniem. Visual Basic umożliwia użycie niejawnego późnego wiązania w kodzie. Kompilator Visual Basic wywołuje metodę pomocnika, która używa odbicia w celu uzyskania typu obiektu. Argumenty przekazane do metody pomocnika powodują wywołanie odpowiedniej metody w czasie wykonywania. Te argumenty są wystąpieniem (obiektem), na którym należy wywołać metodę, nazwę wywołanej metody (ciąg) i argumenty przekazane do wywołanej metody (tablicę obiektów).  
  
 W poniższym przykładzie kompilator Visual Basic używa odbicia niejawnie do wywołania metody w obiekcie, którego typ nie jest znany w czasie kompilacji. Klasa **HelloWorld** ma metodę **PrintHello** , która drukuje "Hello World" połączone z tekstem, który jest przesyłany do metody **PrintHello** . Metoda **PrintHello** wywołana w tym przykładzie jest w rzeczywistości a <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>; kod Visual Basic umożliwia wywoływanie metody **PrintHello** , tak jakby typ obiektu (helloObj) był znany w czasie kompilacji (wczesne wiązanie), a nie w czasie wykonywania ( Późne wiązanie).  
  
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
 Oprócz użycia niejawnie przez kompilatory dla późnego wiązania, odbicie może być używane jawnie w kodzie do osiągnięcia późnego wiązania.  
  
 [Środowisko uruchomieniowe języka wspólnego](../../standard/clr.md) obsługuje wiele języków programowania, a reguły powiązań tych języków różnią się. W przypadku wczesnej ograniczonej wielkości generatory kodu mogą całkowicie kontrolować to powiązanie. Jednak w późnym łączeniu poprzez odbicie powiązanie musi być kontrolowane przez dostosowane powiązanie. <xref:System.Reflection.Binder> Klasa zawiera niestandardową kontrolkę wyboru elementu członkowskiego i wywołania.  
  
 Przy użyciu powiązania niestandardowego można załadować zestaw w czasie wykonywania, uzyskać informacje o typach w tym zestawie, określić typ, a następnie wywołać metody lub uzyskać dostęp do pól lub właściwości tego typu. Ta technika jest przydatna, jeśli nie znasz typu obiektu w czasie kompilacji, na przykład gdy typ obiektu jest zależny od danych wejściowych użytkownika.  
  
 Poniższy przykład ilustruje prosty niestandardowy spinacz, który nie zapewnia konwersji typu argumentu. `Simple_Type.dll` Kod poprzedzający główny przykład. Pamiętaj, aby skompilować `Simple_Type.dll` , a następnie dołączyć odwołanie do niego w projekcie w czasie kompilacji.  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### <a name="invokemember-and-createinstance"></a>InvokeMember i CreateInstance  
 Służy <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType> do wywoływania elementu członkowskiego typu. Metody **CreateInstance** różnych klas, takie jak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> i <xref:System.Reflection.Assembly.CreateInstance%2A?displayProperty=nameWithType>, są wyspecjalizowanymi formami **InvokeMember** , które tworzą nowe wystąpienia określonego typu. Klasa **spinacza** jest używana na potrzeby rozpoznawania przeciążenia i przekształcania argumentów w tych metodach.  
  
 Poniższy przykład pokazuje trzy możliwe kombinacje przekształcenia argumentów (konwersja typu) i wybór elementu członkowskiego. W przypadku 1 nie jest wymagana Konwersja argumentów ani wybór elementu członkowskiego. W przypadku 2 wymagany jest tylko wybór elementu członkowskiego. W przypadku 3 jest wymagana tylko wymuszone przekształcenie argumentu.  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 Jeśli jest dostępny więcej niż jeden element członkowski o tej samej nazwie, jest wymagana rozdzielczość przeciążenia. Metody <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=nameWithType> i<xref:System.Reflection.Binder.BindToField%2A?displayProperty=nameWithType> służą do rozpoznawania powiązań z pojedynczym elementem członkowskim. Obiekt **Binder. BindToMethod** udostępnia również rozpoznawanie właściwości poprzez metody dostępu do właściwości **Get** i **Set** .  
  
 **BindToMethod** zwraca <xref:System.Reflection.MethodBase> element do Invoke lub odwołanie o wartości null (**Nothing** w Visual Basic), jeśli takie wywołanie nie jest możliwe. Wartość zwracana **element MethodBase** nie musi być jedną z tych zawartych w parametrze *Match* , chociaż jest to zwykły przypadek.  
  
 Gdy są obecne argumenty ByRef, obiekt wywołujący może chcieć uzyskać zwrot. W związku z tym, **spinacz** umożliwia klientowi mapowanie tablicy argumentów z powrotem do oryginalnej postaci, jeśli **BindToMethod** operuje tablicą argumentów. Aby to zrobić, obiekt wywołujący musi mieć gwarancję, że kolejność argumentów nie jest zmieniana. Gdy argumenty są przekazane według nazwy, **spinacz** zmienia kolejność tablic argumentów i jest to, co obiekt wywołujący widzi. Aby uzyskać więcej informacji, zobacz <xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=nameWithType>.  
  
 Zestaw dostępnych elementów członkowskich to elementy członkowskie zdefiniowane w typie lub dowolnym typie podstawowym. Jeśli <xref:System.Reflection.BindingFlags> jest określony, elementy członkowskie dowolnego ułatwienia dostępu zostaną zwrócone w zestawie. Jeśli **BindingFlags. inpublic** nie jest określony, spinacz musi wymusić reguły ułatwień dostępu. Podczas określania **publicznej** lub niepublicznej flagi powiązania należy również określić **wystąpienie** lub flagę powiązania **statycznego** albo nie zwraca żadnych elementów członkowskich.  
  
 Jeśli istnieje tylko jeden element członkowski danej nazwy, wywołanie zwrotne nie jest wymagane, a powiązanie jest wykonywane dla tej metody. Przypadek 1 przykładu kodu ilustruje ten punkt: Dostępna jest tylko jedna metoda **PrintBob** i dlatego nie jest konieczne wywołanie zwrotne.  
  
 Jeśli istnieje więcej niż jeden element członkowski w dostępnym zestawie, wszystkie te metody są przesyłane do **BindToMethod**, co wybiera odpowiednią metodę i zwraca ją. W przypadku 2 przykładowego kodu istnieją dwie metody o nazwie **PrintValue**. Odpowiednia metoda jest wybierana przez wywołanie do **BindToMethod**.  
  
 <xref:System.Reflection.Binder.ChangeType%2A>wykonuje przekształcenie argumentu (konwersja typu), które konwertuje rzeczywiste argumenty na typ argumentów formalnych wybranej metody. **ChangeType** jest wywoływana dla każdego argumentu, nawet jeśli typy pasują dokładnie.  
  
 W przypadku 3 przykładu kodu rzeczywisty argument typu **String** o wartości "5,5" jest przenoszona do metody z formalnym argumentem typu **Double**. Aby wywołanie zakończyło się pomyślnie, wartość ciągu "5,5" musi być konwertowana na wartość typu Double. **ChangeType** wykonuje tę konwersję.  
  
 **ChangeType** wykonuje tylko [przekształcenia](../../standard/base-types/type-conversion.md)bezstratne lub rozszerzające, jak pokazano w poniższej tabeli.  
  
|Typ źródła|Typ docelowy|  
|-----------------|-----------------|  
|Dowolny typ|Jego typ podstawowy|  
|Dowolny typ|Interfejs, który implementuje|  
|Char|UInt16, UInt32, Int32, UInt64, Int64, Single, Double|  
|Byte|Char, UInt16, Int16, UInt32, Int32, UInt64, Int64, Single, Double|  
|SByte|Int16, Int32, Int64, Single, Double|  
|UInt16|UInt32, Int32, UInt64, Int64, Single, Double|  
|Int16|Int32, Int64, Single, Double|  
|UInt32|UInt64, Int64, Single, Double|  
|Int32|Int64, pojedyncze, podwójne|  
|UInt64|Pojedyncza, Podwójna|  
|Int64|Pojedyncza, Podwójna|  
|Single|Double|  
|Typ niereferencyjny|Typ referencyjny|  
  
 Klasa ma metody **Get** , które używają parametrów typu spinacza do rozpoznawania odwołań do określonego elementu członkowskiego. <xref:System.Type> <xref:System.Type.GetConstructor%2A?displayProperty=nameWithType>, <xref:System.Type.GetMethod%2A?displayProperty=nameWithType> i<xref:System.Type.GetProperty%2A?displayProperty=nameWithType> wyszukiwanie określonego elementu członkowskiego bieżącego typu przez podanie informacji o sygnaturze dla tego elementu członkowskiego. <xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=nameWithType>i <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=nameWithType> są wywoływane z powrotem w celu wybrania informacji o podpisie odpowiednich metod.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type.InvokeMember%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Konwersja typu w .NET Framework](../../standard/base-types/type-conversion.md)
