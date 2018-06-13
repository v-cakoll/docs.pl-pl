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
ms.openlocfilehash: 2efa8cfb2b196d6f5a26354161e42c1f376e43b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389542"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a>Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera
Zezwalaj na wyświetlanie atrybutów debugera dewelopera typu, który określa i najlepiej rozumie zachowania w czasie wykonywania tego typu, można również określić, jakie tego typu będą wyglądać po wyświetleniu go w debugerze. Ponadto debuger wyświetlić atrybuty, które zapewniają `Target` właściwości można zastosować na poziomie zestawu przez użytkowników bez wiedzy o kodzie źródłowym. <xref:System.Diagnostics.DebuggerDisplayAttribute> Atrybut kontroluje sposób wyświetlania typu lub elementu członkowskiego w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerBrowsableAttribute> Atrybut określa, czy i jak pole lub właściwość jest wyświetlana w oknach zmiennych debugera. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut określa typu zastępczego lub serwer proxy dla typu i zmienia sposób typ jest wyświetlana w oknach debugera. Po wyświetleniu zmiennej, która jest serwer proxy lub typu zastępczego serwera proxy dla oryginalnego typu w okna debugera oznacza **.** Wpisz windowdisplays zmiennych debugera tylko publiczne elementy członkowskie serwera proxy. Prywatne elementy członkowskie nie są wyświetlane.  
  
## <a name="using-the-debuggerdisplayattribute"></a>Przy użyciu debuggerdisplayattribute —  
 <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor ma jeden argument: ciąg mają być wyświetlane w kolumnie wartość dla wystąpienia typu. Ten ciąg może zawierać nawiasy klamrowe ({i}). Tekst w parę nawiasów klamrowych jest szacowana jako wyrażenie. Na przykład następujący kod C# spowoduje "Count = 4" do wyświetlenia, gdy zaznaczona jest znak plus (+), aby rozwinąć debugera dla wystąpienia `MyHashtable`.  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 Atrybuty stosowane do właściwości, do którego odwołuje się wyrażenie, które nie zostały przetworzone. Dla kompilatora C# ogólne wyrażenia jest dozwolone, który ma niejawne dostęp tylko do tego odwołania dla bieżącego wystąpienia typu docelowego. Wyrażenie jest ograniczona. Brak dostępu do aliasy, zmienne lokalne lub wskaźniki nie istnieje. W kodzie języka C#, można użyć ogólne wyrażenia w nawiasach klamrowych, które ma niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typ docelowy.  
  
 Na przykład, jeśli obiekt C# została zastąpiona `ToString()`, debuger wywoła zastąpienie i wyświetlić jej wynik, zamiast standardowego `{<typeName>}.` związku z tym, jeśli ma być zastąpiona `ToString()`, nie trzeba używać <xref:System.Diagnostics.DebuggerDisplayAttribute>. Jeśli używasz zarówno <xref:System.Diagnostics.DebuggerDisplayAttribute> atrybut ma pierwszeństwo przed `ToString()` zastąpienia.  
  
## <a name="using-the-debuggerbrowsableattribute"></a>Przy użyciu debuggerbrowsableattribute —  
 Zastosuj <xref:System.Diagnostics.DebuggerBrowsableAttribute> pola lub właściwości w celu określenia, jak pola lub właściwości ma być wyświetlany w oknie debugera. Konstruktor dla tego atrybutu przyjmuje jeden z <xref:System.Diagnostics.DebuggerBrowsableState> wartości wyliczenia, które określa jeden z następujących stanów:  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Never> Wskazuje, że element członkowski nie jest wyświetlany w oknie dane.  Na przykład za pomocą tej wartości dla <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole usuwa pole z hierarchii; pole nie jest wyświetlany po rozwinięciu typu otaczającego, klikając znak plus (+) dla wystąpienia typu.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Wskazuje, że element członkowski jest wyświetlane, ale nie jest domyślnie rozwinięte.  Jest to zachowanie domyślne.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Wskazuje, że ten element członkowski nie jest widoczne, ale obiekty składowe są wyświetlane, gdy jest tablicą lub kolekcją.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> Nie jest obsługiwana przez program Visual Basic w programie .NET Framework w wersji 2.0.  
  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Diagnostics.DebuggerBrowsableAttribute> zapobiegające właściwości po znajdujących się w oknie debugowania dla klasy.  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a>Przy użyciu DebuggerTypeProxy  
 Użyj <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutu, gdy trzeba znacznie i całkowicie zmienić widok debugowania typu, lecz nie zmieniać samego typu. <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atrybut służy do określania wyświetlania serwera proxy dla typu, dzięki czemu Deweloper dostosować widok dla danego typu.  Ten atrybut tak samo, jak <xref:System.Diagnostics.DebuggerDisplayAttribute>, można na poziomie zestawu, w którym to przypadku <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> właściwość określa typ, dla którego będzie można używać serwera proxy. Zalecane użycie jest, że ten atrybut określa prywatnej typu zagnieżdżonego w typie, do którego zastosowano atrybut.  Ewaluatora wyrażeń, aby obsługuje typ przeglądarki sprawdza dla tego atrybutu, gdy typem jest wyświetlana. Jeśli ten atrybut zostanie znaleziony, ewaluatora wyrażenia zastępuje wyświetlania typ serwera proxy dla ten atrybut jest stosowany do typu.  
  
 Gdy <xref:System.Diagnostics.DebuggerTypeProxyAttribute> jest obecny, okno zmiennych debugera zawiera tylko publiczne elementy członkowskie typu serwera proxy. Prywatne elementy członkowskie nie są wyświetlane. Zachowanie okna danych nie ulega zmianie przez rozszerzony atrybut widoki.  
  
 Aby uniknąć kar za niepotrzebne wydajności, atrybutów wyświetlania serwera proxy nie są przetwarzane aż obiekt jest rozwinięty przez użytkownika, klikając znak plus (+) obok typu w oknie danych lub poprzez zastosowanie <xref:System.Diagnostics.DebuggerBrowsableAttribute> atrybut. W związku z tym zaleca się, że atrybuty nie można zastosować do typu ekranu. Atrybuty można i powinny być stosowane w treści typu wyświetlania.  
  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Aby określić typ ma być używany jako serwer proxy wyświetlania debugera.  
  
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
 Poniższy przykład kodu można wyświetlać w [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] aby zobaczyć wyniki zastosowania <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, i <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atrybutów.  
  
### <a name="code"></a>Kod  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
