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
ms.openlocfilehash: 4150658f713e626c5578c21cfada0f6410cbd37b
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873258"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera

Atrybutów wyświetlania debugera umożliwia deweloperowi typu, który określa się oraz zrozumiał najlepiej zachowanie środowiska uruchomieniowego tego typu, można również określić, jakie tego typu będzie wyglądać po wyświetleniu go w debugerze. Ponadto debuger wyświetlić atrybuty, które zapewniają `Target` właściwość może zostać zastosowana na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego. <xref:System.Diagnostics.DebuggerDisplayAttribute> Atrybut kontroluje sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Atrybut określa, czy i jak pole lub właściwość jest wyświetlana w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typu zastępczego lub serwera proxy dla typu i zmienia sposób typu jest wyświetlana w oknach debugera. Po wyświetleniu zmiennej, która ma serwer proxy lub typu zastępczego oznacza serwera proxy oryginalnego typu w okna debugera. W oknie zmiennych debugera zostaną wyświetlone tylko publiczne składowe typ serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Za pomocą debuggerdisplayattribute —  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg, który ma być wyświetlana w kolumnie wartość dla wystąpienia typu. Ten ciąg może zawierać nawiasy klamrowe ({i}). Tekst w parę nawiasów klamrowych jest oceniane jako wyrażenie. Na przykład, poniższy kod C# powoduje "liczba = 4" będzie wyświetlana po wybraniu znak plus (+), aby rozwinąć debugera dla wystąpienia `MyHashtable`.  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atrybuty stosowane do właściwości, do którego odwołuje się wyrażenie nie są przetwarzane. Dla kompilatora C# ogólnego wyrażenia jest dozwolone, który ma niejawne dostęp tylko do tego odwołania dla bieżącego wystąpienia typu docelowego. Wyrażenie jest ograniczona. Brak dostępu do aliasów, zmienne lokalne lub wskaźniki. W kodzie języka C#, można użyć wyrażenia ogólnych między nawiasy klamrowe, które ma niejawne dostęp do `this` wskaźnik dla bieżącego wystąpienia na typ docelowy.

Na przykład, jeśli obiekt C# została zastąpiona `ToString()`, debuger wywoła zastępowania i wyświetlić jego wynik zamiast standardowego `{<typeName>}.` Thus, jeśli zastępowano `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>. Jeśli używasz zarówno <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` zastąpienia.

## <a name="using-the-debuggerbrowsableattribute"></a>Za pomocą debuggerbrowsableattribute —
 Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola lub właściwości w celu określenia, jak pole lub właściwość ma być wyświetlana w oknie debugera. Konstruktor dla tego atrybutu ma jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, które określa jedno z następujących stanów:

-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> Wskazuje, że element członkowski nie jest wyświetlany w oknie dane.  Na przykład za pomocą tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typ otaczający, klikając znak plus (+) dla wystąpienia typu.

-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Wskazuje, że element członkowski jest wyświetlane, ale nie jest domyślnie rozwinięte.  Jest to zachowanie domyślne.

-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Wskazuje, że ten element członkowski nie jest wyświetlana, ale obiekty składowe są wyświetlane w przypadku tablicy lub kolekcji.

> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Nie jest obsługiwana przez program Visual Basic w programie .NET Framework 2.0.

Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerBrowsableAttribute> zapobiegające właściwość postępując znajdujących się w oknie Debugowanie dla tej klasy.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Za pomocą DebuggerTypeProxy
 Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacznie i całkowicie zmienić widok debugowania typu, ale nie zmienianie samego typu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut jest używany do określenia wyświetlania serwera proxy dla typu, co zatem programistą, aby dostosować widok dla danego typu.  Ten atrybut, takie jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, może służyć na poziomie zestawu, w którym to przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> właściwość określa typ, dla której będzie używany serwer proxy. Zalecane użycie jest, że ten atrybut określa prywatnej typu zagnieżdżonego, występujący w przypadku typu jest stosowany.  Ewaluatora wyrażeń, aby obsługuje typ osoby przeglądające sprawdza dla tego atrybutu, gdy typem jest wyświetlana. Jeśli ten atrybut zostanie znaleziony, Ewaluator wyrażeń zastępuje wyświetlaną typ serwera proxy dla typu, który jest stosowany.

 Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, w oknie zmiennych debugera, zostaną wyświetlone tylko publiczne składowe typ serwera proxy. Prywatne elementy członkowskie nie są wyświetlane. Zachowanie okna danych nie jest zmieniany przy użyciu funkcji widoków rozszerzonych atrybutów.

 Aby uniknąć spadku wydajności niepotrzebne, atrybutów wyświetlania serwera proxy nie zostały przetworzone, dopóki obiekt jest rozwinięta, przez użytkownika, klikając znak plus (+) obok typu w oknie danych lub przez zastosowanie <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut. W związku z tym zaleca się, że żadne atrybuty można zastosować do typu ekranu. Atrybuty można i powinny być stosowane w ramach organu typ wyświetlania.

 Poniższy przykład kodu pokazuje użycie <xref:System.Diagnostics.DebuggerTypeProxyAttribute> do określania typu ma być używany jako serwer proxy wyświetlania debugera.

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

Poniższy przykład kodu mogą być wyświetlane w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutów.

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>