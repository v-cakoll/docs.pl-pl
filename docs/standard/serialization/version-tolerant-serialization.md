---
title: "Serializacji z tolerancją dla wersji"
ms.date: 08/08/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 90f2b1e73a24b0f732eaba4422faa9a1dcc15135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization"></a>Serializacji z tolerancją dla wersji
W wersji 1.0, 1.1 programu .NET Framework Tworzenie typów możliwych do serializacji, które będą wielokrotnego użytku z jednej wersji aplikacji do następnego był kłopotliwy. Jeśli typ został zmodyfikowany przez dodanie pola dodatkowe, wystąpi następujących problemów:  
  
-   Starsze wersje aplikacji czy zgłaszają wyjątki monit o nowe wersje stary typ do deserializacji.  
  
-   Nowsze wersje aplikacji spowoduje zgłoszenie wyjątków podczas deserializacji starsze wersje tego typu z brakującymi danymi.  
  
 Wersja na uszkodzenia serializacji (SRS) to zestaw funkcje wprowadzone w programie .NET Framework 2.0, który ułatwia, wraz z upływem czasu, aby zmodyfikować typów możliwych do serializacji. W szczególności funkcje SRS są włączone dla klasy, do którego <xref:System.SerializableAttribute> zastosowano atrybut, w tym typów ogólnych. SRS sprawia, że można dodać nowe pola do tych klas bez przerywania zgodność z innymi wersjami tego typu. Przykładową aplikację pracy, zobacz [wersji odporna na przykład technologii serializacji](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).  
  
 Funkcje SRS są włączone, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Ponadto wszystkie funkcje, z wyjątkiem tolerancja nadmiarowe dane są również włączone podczas korzystania z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Aby uzyskać więcej informacji o używaniu tych klas serializacji, zobacz [szeregowanie binarne](binary-serialization.md).  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Lista funkcji.  
 Zestaw funkcji obejmuje następujące czynności:  
  
-   Tolerancja danych zewnętrznych lub nieoczekiwany. Dzięki temu nowszych wersji typu wysyłać dane do starszych wersji.  
  
-   Tolerancja brakujących opcjonalnymi danymi. Dzięki temu starszych wersji wysyłać dane do nowszych wersji.  
  
-   Serializacja wywołania zwrotne. Dzięki temu inteligentną domyślne ustawienie wartości w przypadkach, gdy jest Brak danych.  
  
 Ponadto to funkcja do deklarowania, gdy zostało dodane nowe pole opcjonalne. Jest to <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> właściwości <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu.  
  
 Te funkcje opisano szczegółowo poniżej.  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a>Tolerancja nadmiarowe lub nieoczekiwane dane  
 W przeszłości podczas deserializacji wszelkie dane nadmiarowe lub nieoczekiwany spowodowane wyjątki zostanie wygenerowany. Z SRS w tej samej sytuacji, wszelkie dane nadmiarowe lub nieoczekiwany jest ignorowana zamiast powoduje wyjątki zostanie wygenerowany. Dzięki temu aplikacje, które korzystają z nowszych wersji typu (to znaczy, wersja, którą zawiera więcej pól) do wysyłania informacji do aplikacji, które oczekują starsze wersje tego samego typu.  
  
 W poniższym przykładzie dodatkowe dane zawarte w `CountryField` wersji 2.0 `Address` klasy jest ignorowane w przypadku starszych aplikacji deserializuje nowszej wersji.  
  
```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  
  
## <a name="tolerance-of-missing-data"></a>Brak danych na uszkodzenia  
 Pola może zostać oznaczona jako opcjonalna, stosując <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do nich. Podczas deserializacji Jeśli brakuje danych opcjonalny mechanizm serializacji ignoruje braku i nie zgłoszony wyjątek. W związku z tym aplikacje, które oczekują starsze wersje typu może wysyłać dane do aplikacji, które oczekują nowsze wersje tego samego typu.  
  
 W poniższym przykładzie przedstawiono wersja 2.0 `Address` klasy z `CountryField` oznaczona jako opcjonalna, pola. Jeśli starszych aplikacji w wersji 1 są wysyłane do nowszej aplikacji, która oczekuje w wersji 2.0, braku danych jest ignorowana.  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
  
    [OptionalField]  
    public string CountryField;  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
  
    <OptionalField> _  
    Public CountryField As String  
End Class  
```  
  
## <a name="serialization-callbacks"></a>Wywołania zwrotne serializacji  
 Serializacja wywołania zwrotne są mechanizm udostępniająca punkty zaczepienia z procesem serializacji/deserializacji w cztery punkty.  
  
|Atrybut|Gdy jest wywoływana metoda skojarzone|Typowym zastosowaniem|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Przed deserialization.*|Zainicjuj wartości domyślne dla pola opcjonalne.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Po deserializacji.|Usuń zawartość wszystkich innych pól w oparciu o wartości pola opcjonalne.|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Przed serializacji.|Przygotowanie do serializacji. Na przykład utworzyć struktury danych opcjonalne.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Po serializacji.|Rejestrowanie zdarzeń serializacji.|  
  
 \*To wywołanie zwrotne jest wywoływane przed konstruktorze deserializacji, jeśli jest dostępny.  
  
### <a name="using-callbacks"></a>Za pomocą wywołania zwrotne  
 Aby korzystać z wywołań zwrotnych, zastosuj odpowiedni atrybut do metody, która akceptuje <xref:System.Runtime.Serialization.StreamingContext> parametru. Może być oznaczony tylko jednej metody na klasy z każdym z tych atrybutów. Na przykład:  
  
```csharp  
[OnDeserializing]  
private void SetCountryRegionDefault(StreamingContext sc)  
{  
    CountryField = "Japan";  
}  
```  
  
```vb  
<OnDeserializing>  
Private Sub SetCountryRegionDefault(StreamingContext sc)  
    CountryField = "Japan";  
End Sub  
```  
  
 Przeznaczeniem z tych metod jest przechowywania wersji. Podczas deserializacji to opcjonalne pole może nie być poprawnie zainicjować w przypadku braku danych dla tego pola. Ten problem można rozwiązać przez tworzenie metody, która przypisuje wartość poprawne, a następnie zastosowanie albo **OnDeserializingAttribute** lub **OnDeserializedAttribute** atrybut do metody.  
  
 Poniższy przykład przedstawia metodę w kontekście typu. Jeśli starszej wersji aplikacji wysyła wystąpienia `Address` klasy do nowszej wersji aplikacji, `CountryField` danych pola będą niedostępne. Ale po deserializacji, pola zostanie ustawiona na wartość domyślną "Japonia".  
  
```csharp  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    [OptionalField]  
    public string CountryField;  
  
    [OnDeserializing]  
    private void SetCountryRegionDefault (StreamingContext sc)  
    {  
        CountryField = "Japan";  
    }  
}  
```  
  
```vb  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    <OptionalField> _  
    Public CountryField As String  
  
    <OnDeserializing> _  
    Private Sub SetCountryRegionDefault(StreamingContext sc)  
        CountryField = "Japan";  
    End Sub  
End Class  
```  
  
## <a name="the-versionadded-property"></a>Właściwość VersionAdded  
 **OptionalFieldAttribute** ma **VersionAdded** właściwości. W wersji 2.0 programu .NET Framework to nie jest używany. Jednak należy poprawnie ustawić tę właściwość, aby upewnić się, że typ będzie zgodna z aparaty przyszłych serializacji.  
  
 Właściwość wskazuje, której wersji dodano pole danego typu. Powinien być zwiększany o dokładnie jeden (rozpoczyna się od 2) zawsze zmodyfikować typu, jak pokazano w poniższym przykładzie:  
  
```csharp  
// Version 1.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
}  
  
// Version 2.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded = 2)]  
    public string NickName;  
    [OptionalField(VersionAdded = 2)]  
    public DateTime BirthDate;  
}  
  
// Version 3.0  
[Serializable]  
public class Person  
{  
    public string FullName;  
  
    [OptionalField(VersionAdded=2)]  
    public string NickName;  
    [OptionalField(VersionAdded=2)]  
    public DateTime BirthDate;  
  
    [OptionalField(VersionAdded=3)]  
    public int Weight;  
}  
```  
  
```vb  
' Version 1.0  
<Serializable> _  
Public Class Person  
    Public FullName  
End Class  
  
' Version 2.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
End Class  
  
' Version 3.0  
<Serializable> _  
Public Class Person  
    Public FullName As String  
  
    <OptionalField(VersionAdded := 2)> _  
    Public NickName As String  
    <OptionalField(VersionAdded := 2)> _  
    Public BirthDate As DateTime  
  
    <OptionalField(VersionAdded := 3)> _  
    Public Weight As Integer  
End Class  
```  
  
## <a name="serializationbinder"></a>SerializationBinder  
 Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, ponieważ wymagana jest nieco innej klasy w serwera i klienta. <xref:System.Runtime.Serialization.SerializationBinder>Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji.  Aby użyć tej klasy, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 W celu zapewnienia zachowania właściwej wersji, modyfikując typu od wersji należy wykonać następujące czynności:  
  
-   Nigdy nie należy usunąć pole serializacji.  
  
-   Nigdy nie stosuj <xref:System.NonSerializedAttribute> atrybutu do pola, jeśli ten atrybut nie została zastosowana do pola w poprzedniej wersji.  
  
-   Nigdy nie można zmienić nazwy lub typu serializacji pola.  
  
-   Podczas dodawania nowego pola serializacji, zastosuj **OptionalFieldAttribute** atrybutu.  
  
-   Podczas usuwania **NonSerializedAttribute** atrybutu z pola (który nie był możliwy do serializacji w poprzedniej wersji), są stosowane **OptionalFieldAttribute** atrybutu.  
  
-   Dla wszystkich pól opcjonalnych, określ opisową ustawienia domyślne, za pomocą wywołania zwrotne serializacji, chyba że 0 lub **null** jako wartości domyślne są dozwolone.  
  
 W celu zapewnienia, że typem będzie zgodna z aparatów przyszłych serializacji, postępuj zgodnie z tymi wytycznymi dotyczącymi:  
  
-   Zawsze wartość **VersionAdded** właściwość **OptionalFieldAttribute** atrybutu nieprawidłowo.  
  
-   Unikaj rozgałęziony przechowywania wersji.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.SerializableAttribute>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>  
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 <xref:System.NonSerializedAttribute>  
 [Serializacja binarna](binary-serialization.md)
