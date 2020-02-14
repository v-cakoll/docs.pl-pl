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
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216491"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera

Atrybuty wyświetlania debugera umożliwiają deweloperom typu, którzy określają i najlepiej rozumieją zachowanie środowiska uruchomieniowego tego typu, aby określić, jaki typ będzie wyglądać, gdy zostanie on wyświetlony w debugerze. Ponadto atrybuty wyświetlania debugera, które udostępniają Właściwość `Target`, mogą być stosowane na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego. Atrybut <xref:System.Diagnostics.DebuggerDisplayAttribute> kontroluje sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera. Atrybut <xref:System.Diagnostics.DebuggerBrowsableAttribute> określa, czy i w jaki sposób pole lub właściwość są wyświetlane w oknach zmiennych debugera. Atrybut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> określa typ substytutu lub serwer proxy dla typu i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy lub typ zastępczy, serwer proxy znajduje się dla oryginalnego typu w oknie wyświetlania debugera. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Korzystanie z DebuggerDisplayAttribute —  

Konstruktor <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> ma jeden argument: ciąg, który ma być wyświetlany w kolumnie value dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe ({i}). Tekst w parze nawiasów klamrowych jest obliczany jako wyrażenie. Na przykład poniższy C# kod powoduje, że wartość "Count = 4" będzie wyświetlana po wybraniu znaku plus (+) w celu rozwinięcia wyświetlania debugera dla wystąpienia `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atrybuty zastosowane do właściwości, do których odwołuje się wyrażenie, nie są przetwarzane. W przypadku C# kompilatora jest dozwolone wyrażenie ogólne, które ma tylko niejawny dostęp do tego odwołania dla bieżącego wystąpienia typu docelowego. Wyrażenie jest ograniczone; nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników. W C# kodzie można użyć wyrażenia ogólnego między nawiasami klamrowymi, które mają niejawny dostęp do wskaźnika `this` tylko dla bieżącego wystąpienia typu docelowego.

Na przykład jeśli C# obiekt ma zastąpioną `ToString()`, debuger wywoła przesłonięcie i pokaże jego wynik zamiast standardowego `{<typeName>}.` w związku z tym, jeśli zastąpiono `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>. Jeśli używasz obu tych metod, atrybut <xref:System.Diagnostics.DebuggerDisplayAttribute> ma pierwszeństwo przed przesłonięciem `ToString()`.

## <a name="using-the-debuggerbrowsableattribute"></a>Korzystanie z DebuggerBrowsableAttribute
 Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> do pola lub właściwości, aby określić, w jaki sposób pole lub właściwość mają być wyświetlane w oknie debugera. Konstruktor dla tego atrybutu przyjmuje jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, która określa jeden z następujących stanów:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never> wskazuje, że element członkowski nie jest wyświetlany w oknie danych.  Na przykład użycie tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> w polu spowoduje usunięcie pola z hierarchii; pole nie jest wyświetlane po rozwinięciu typu otaczającego przez kliknięcie znaku plus (+) dla wystąpienia typu.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> wskazuje, że element członkowski jest wyświetlany, ale nie jest domyślnie rozwinięty.  To zachowanie domyślne.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> wskazuje, że sama składowa nie jest wyświetlana, ale jego obiekty składowe są wyświetlane, jeśli jest tablicą lub kolekcją.

> [!NOTE]
> <xref:System.Diagnostics.DebuggerBrowsableAttribute> nie jest obsługiwana przez Visual Basic w .NET Framework wersji 2,0.

Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute>, aby zapobiec wyświetlaniu właściwości, która nie jest wyświetlana w oknie debugowania dla klasy.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Korzystanie z DebuggerTypeProxy
 Użyj atrybutu <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, gdy trzeba znacząco i w sposób istotny zmienić widok debugowania typu, ale nie zmieniać samego typu. Atrybut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> służy do określania serwera proxy dla typu, co umożliwia deweloperom Dostosowywanie widoku dla tego typu.  Ten atrybut, taki jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, może być używany na poziomie zestawu, w tym przypadku Właściwość <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> określa typ, dla którego będzie używany serwer proxy. Zalecane użycie polega na tym, że ten atrybut określa prywatny Typ zagnieżdżony, który występuje w typie, do którego zastosowano atrybut.  Ewaluatora wyrażeń, które obsługują osoby przeglądające typy sprawdzają ten atrybut, gdy zostanie wyświetlony typ. Jeśli atrybut zostanie znaleziony, ewaluatora wyrażeń zastępuje typ wyświetlanego serwera proxy dla typu, do którego zastosowano atrybut.

 Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, w oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane. Zachowanie okna dane nie jest zmieniane przez widoki z rozszerzonymi atrybutami.

 Aby uniknąć niepotrzebnych kar z wydajnością, atrybuty wyświetlanego serwera proxy nie są przetwarzane do momentu, gdy obiekt zostanie rozwinięty, przez kliknięcie przez użytkownika kliknięcia znaku plusa (+) obok typu w oknie danych lub przez zastosowanie atrybutu <xref:System.Diagnostics.DebuggerBrowsableAttribute>. Dlatego zaleca się, aby nie stosować atrybutów do typu wyświetlanego. Atrybuty mogą i powinny być stosowane w treści typu wyświetlania.

 Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, aby określić typ, który ma być używany jako serwer proxy wyświetlania debugera.

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

Poniższy przykład kodu można wyświetlić w programie Visual Studio, aby zobaczyć wyniki zastosowania atrybutów <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>i <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
