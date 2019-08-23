---
title: Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c27732de448e19c4227062706c7a7d73c98e5f19
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966878"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera

Atrybuty wyświetlania debugera umożliwiają deweloperom typu, którzy określają i najlepiej rozumieją zachowanie środowiska uruchomieniowego tego typu, aby określić, jaki typ będzie wyglądać, gdy zostanie on wyświetlony w debugerze. Dodatkowo debuger wyświetla atrybuty, które udostępniają `Target` właściwość, można stosować na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego. Ten <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut określa sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera. Ten <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut określa, czy i w jaki sposób pole lub właściwość są wyświetlane w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typ substytutu lub serwer proxy dla typu i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy lub typ zastępczy, serwer proxy znajduje się dla oryginalnego typu w oknie wyświetlania debugera. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Korzystanie z DebuggerDisplayAttribute —  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg, który ma być wyświetlany w kolumnie wartości dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe ({i}). Tekst w parze nawiasów klamrowych jest obliczany jako wyrażenie. Na przykład poniższy C# kod powoduje, że wartość "Count = 4" będzie wyświetlana po wybraniu znaku plus (+), aby rozwinąć debuger wyświetlany dla wystąpienia `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atrybuty zastosowane do właściwości, do których odwołuje się wyrażenie, nie są przetwarzane. W przypadku C# kompilatora jest dozwolone wyrażenie ogólne, które ma tylko niejawny dostęp do tego odwołania dla bieżącego wystąpienia typu docelowego. Wyrażenie jest ograniczone; nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników. W C# kodzie można użyć wyrażenia ogólnego między nawiasami klamrowymi, które mają niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typu docelowego.

Na przykład C# Jeśli obiekt został zastąpiony `ToString()`, debuger wywoła przesłonięcie i pokaże wynik zamiast standardowego `{<typeName>}.` , w związku z tym, jeśli został zastąpiony `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>. Jeśli używasz obu tych metod, <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` przesłonięciem.

## <a name="using-the-debuggerbrowsableattribute"></a>Korzystanie z DebuggerBrowsableAttribute
 <xref:System.Diagnostics.DebuggerBrowsableAttribute> Zastosuj do pola lub właściwości, aby określić, w jaki sposób pole lub właściwość mają być wyświetlane w oknie debugera. Konstruktor dla tego atrybutu przyjmuje jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, która określa jeden z następujących stanów:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never>wskazuje, że element członkowski nie jest wyświetlany w oknie dane.  Na przykład użycie tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola w polu usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typu otaczającego przez kliknięcie znaku plus (+) dla wystąpienia typu.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>wskazuje, że element członkowski jest wyświetlany, ale nie jest domyślnie rozwinięty.  Jest to zachowanie domyślne.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>wskazuje, że sama składowa nie jest wyświetlana, ale jego obiekty składowe są wyświetlane, jeśli jest tablicą lub kolekcją.

> [!NOTE]
> Program <xref:System.Diagnostics.DebuggerBrowsableAttribute> nie jest obsługiwany przez Visual Basic w .NET Framework wersja 2,0.

Poniższy przykład kodu pokazuje użycie elementu, <xref:System.Diagnostics.DebuggerBrowsableAttribute> aby zapobiec wyświetlaniu właściwości, która nie jest wyświetlana w oknie debugowania dla klasy.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Korzystanie z DebuggerTypeProxy
 Użyj atrybutu <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , gdy trzeba znacząco i w sposób istotny zmienić widok debugowania typu, ale nie zmieniać samego typu. Ten <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybut służy do określania serwera proxy dla typu, co umożliwia deweloperom Dostosowywanie widoku dla tego typu.  Ten atrybut, podobnie jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, może być używany na poziomie zestawu, w tym <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> przypadku Właściwość określa typ, dla którego zostanie użyty serwer proxy. Zalecane użycie polega na tym, że ten atrybut określa prywatny Typ zagnieżdżony, który występuje w typie, do którego zastosowano atrybut.  Ewaluatora wyrażeń, które obsługują osoby przeglądające typy sprawdzają ten atrybut, gdy zostanie wyświetlony typ. Jeśli atrybut zostanie znaleziony, ewaluatora wyrażeń zastępuje typ wyświetlanego serwera proxy dla typu, do którego zastosowano atrybut.

 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Gdy jest obecny, w oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane. Zachowanie okna dane nie jest zmieniane przez widoki z rozszerzonymi atrybutami.

 Aby uniknąć niepotrzebnych kar z wydajnością, atrybuty wyświetlanego serwera proxy nie są przetwarzane do momentu, gdy obiekt nie zostanie rozwinięty, przez kliknięcie przez użytkownika kliknięcia znaku plusa (+) obok typu w oknie danych lub przez aplikację <xref:System.Diagnostics.DebuggerBrowsableAttribute> przypisane. Dlatego zaleca się, aby nie stosować atrybutów do typu wyświetlanego. Atrybuty mogą i powinny być stosowane w treści typu wyświetlania.

 Poniższy przykład kodu pokazuje użycie, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> aby określić typ, który ma być używany jako serwer proxy wyświetlania debugera.

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład kodu można wyświetlić w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>atrybutów, <xref:System.Diagnostics.DebuggerBrowsableAttribute>i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
