---
title: Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera
description: Wprowadzenie do atrybutów wyświetlania debugera w programie .NET, które pozwalają deweloperom typu określić, jak będzie wyglądać typ, gdy zostanie on wyświetlony w debugerze.
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
ms.openlocfilehash: f266bf7278f472c51dd355df5ba04a123cbd7df0
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415969"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera

Atrybuty wyświetlania debugera umożliwiają deweloperom typu, którzy określają i najlepiej rozumieją zachowanie środowiska uruchomieniowego tego typu, aby określić, jaki typ będzie wyglądać, gdy zostanie on wyświetlony w debugerze. Dodatkowo debuger wyświetla atrybuty, które udostępniają `Target` Właściwość, można stosować na poziomie zestawu przez użytkowników bez znajomości kodu źródłowego. Ten <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut określa sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera. Ten <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut określa, czy i w jaki sposób pole lub właściwość są wyświetlane w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerTypeProxyAttribute>Atrybut określa typ substytutu lub serwer proxy dla typu i zmienia sposób wyświetlania typu w oknach debugera. Podczas wyświetlania zmiennej, która ma serwer proxy lub typ zastępczy, serwer proxy znajduje się dla oryginalnego typu w oknie wyświetlania debugera. W oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Korzystanie z DebuggerDisplayAttribute —  

<xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A>Konstruktor ma jeden argument: ciąg, który ma być wyświetlany w kolumnie wartości dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe ({i}). Tekst w parze nawiasów klamrowych jest obliczany jako wyrażenie. Na przykład poniższy kod w języku C# powoduje, że wartość "Count = 4" będzie wyświetlana po wybraniu znaku plus (+), aby rozwinąć debuger wyświetlany dla wystąpienia `MyHashtable` .  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

Atrybuty zastosowane do właściwości, do których odwołuje się wyrażenie, nie są przetwarzane. W przypadku kompilatora języka C# wyrażenie ogólne jest dozwolone, które ma tylko niejawny dostęp do tego odwołania dla bieżącego wystąpienia typu docelowego. Wyrażenie jest ograniczone; nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników. W kodzie C# można użyć wyrażenia ogólnego między nawiasy klamrowe, które mają niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typu docelowego.

Na przykład jeśli obiekt języka C# został przesłonięty `ToString()` , debuger wywoła przesłonięcie i pokaże jego wynik zamiast standardowego, w `{<typeName>}.` związku z tym, jeśli został zastąpiony `ToString()` , nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute> . Jeśli używasz obu tych metod, <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` przesłonięciem.

## <a name="using-the-debuggerbrowsableattribute"></a>Korzystanie z DebuggerBrowsableAttribute
 Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> do pola lub właściwości, aby określić, w jaki sposób pole lub właściwość mają być wyświetlane w oknie debugera. Konstruktor dla tego atrybutu przyjmuje jedną z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, która określa jeden z następujących stanów:

- <xref:System.Diagnostics.DebuggerBrowsableState.Never>wskazuje, że element członkowski nie jest wyświetlany w oknie dane.  Na przykład użycie tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola w polu usuwa pole z hierarchii; pole nie jest wyświetlane po rozwinięciu typu otaczającego przez kliknięcie znaku plus (+) dla wystąpienia typu.

- <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>wskazuje, że element członkowski jest wyświetlany, ale nie jest domyślnie rozwinięty.  Jest to zachowanie domyślne.

- <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>wskazuje, że sama składowa nie jest wyświetlana, ale jego obiekty składowe są wyświetlane, jeśli jest tablicą lub kolekcją.

> [!NOTE]
> Program <xref:System.Diagnostics.DebuggerBrowsableAttribute> nie jest obsługiwany przez Visual Basic w .NET Framework wersja 2,0.

Poniższy przykład kodu pokazuje użycie elementu, <xref:System.Diagnostics.DebuggerBrowsableAttribute> Aby zapobiec wyświetlaniu właściwości, która nie jest wyświetlana w oknie debugowania dla klasy.

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a>Korzystanie z DebuggerTypeProxy
 Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacząco i w sposób istotny zmienić widok debugowania typu, ale nie zmieniać samego typu. Ten <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybut służy do określania serwera proxy dla typu, co umożliwia deweloperom Dostosowywanie widoku dla tego typu.  Ten atrybut, podobnie jak <xref:System.Diagnostics.DebuggerDisplayAttribute> , może być używany na poziomie zestawu, w tym przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> Właściwość określa typ, dla którego zostanie użyty serwer proxy. Zalecane użycie polega na tym, że ten atrybut określa prywatny Typ zagnieżdżony, który występuje w typie, do którego zastosowano atrybut.  Ewaluatora wyrażeń, które obsługują osoby przeglądające typy sprawdzają ten atrybut, gdy zostanie wyświetlony typ. Jeśli atrybut zostanie znaleziony, ewaluatora wyrażeń zastępuje typ wyświetlanego serwera proxy dla typu, do którego zastosowano atrybut.

 Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, w oknie zmienna debugera są wyświetlane tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane. Zachowanie okna dane nie jest zmieniane przez widoki z rozszerzonymi atrybutami.

 Aby uniknąć niepotrzebnych kar z wydajnością, atrybuty wyświetlanego serwera proxy nie są przetwarzane do momentu, gdy obiekt zostanie rozwinięty, przez kliknięcie przez użytkownika kliknięcia znaku plusa (+) obok typu w oknie danych lub za pomocą aplikacji <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybutu. Dlatego zaleca się, aby nie stosować atrybutów do typu wyświetlanego. Atrybuty mogą i powinny być stosowane w treści typu wyświetlania.

 Poniższy przykład kodu pokazuje użycie, <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Aby określić typ, który ma być używany jako serwer proxy wyświetlania debugera.

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

Poniższy przykład kodu można wyświetlić w programie Visual Studio, aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute> <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybutów, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> .

### <a name="code"></a>Kod

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
