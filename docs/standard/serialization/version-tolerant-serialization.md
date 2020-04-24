---
title: Serializacja odporna na wersje
ms.date: 08/08/2017
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
ms.openlocfilehash: 9886e2f20ef7954b01ea1f46a9eabdb9ea2cc12d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348435"
---
# <a name="version-tolerant-serialization"></a>Serializacja odporna na wersje

W wersji 1,0 i 1,1 .NET Framework, tworzenie możliwych do przetworzenia typów, które mogą być wielokrotnego użytku z jednej wersji aplikacji do następnej była problematyczne. Jeśli typ został zmodyfikowany przez dodanie pola dodatkowe, wystąpi następujących problemów:

- Starsze wersje aplikacji mogą generować wyjątki, gdy zostanie wyświetlony monit o deserializacja nowych wersji starego typu.
- Nowsze wersje aplikacji spowodują wygenerowanie wyjątków podczas deserializacji starszych wersji typu z brakującymi danymi.

Wersja na uszkodzenia serializacji (SRS) to zestaw funkcje wprowadzone w programie .NET Framework 2.0, który ułatwia, wraz z upływem czasu, aby zmodyfikować typów możliwych do serializacji. W szczególności funkcje SRS są włączone dla klas, do których zastosowano <xref:System.SerializableAttribute> atrybut, w tym typów ogólnych. SRS sprawia, że można dodać nowe pola do tych klas bez przerywania zgodność z innymi wersjami tego typu. Aby uzyskać działającą przykładową aplikację, zobacz [przykład technologii serializacji odpornej na wersje](version-tolerant-serialization-technology-sample.md).

Funkcje SRS są włączone, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Ponadto wszystkie funkcje, z wyjątkiem tolerancja nadmiarowe dane są również włączone podczas korzystania z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Aby uzyskać więcej informacji o używaniu tych klas do serializacji, zobacz [Serializacja binarna](binary-serialization.md).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Lista funkcji

Zestaw funkcji obejmuje następujące czynności:

- Tolerancja danych zewnętrznych lub nieoczekiwany. Dzięki temu nowszych wersji typu wysyłać dane do starszych wersji.
- Tolerancja brakujących opcjonalnymi danymi. Dzięki temu starszych wersji wysyłać dane do nowszych wersji.
- Serializacja wywołania zwrotne. Dzięki temu inteligentną domyślne ustawienie wartości w przypadkach, gdy jest Brak danych.

Ponadto to funkcja do deklarowania, gdy zostało dodane nowe pole opcjonalne. Jest to <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> właściwości <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu.

Te funkcje zostały omówione bardziej szczegółowo w poniższych sekcjach.

### <a name="tolerance-of-extraneous-or-unexpected-data"></a>Tolerancja niektórych lub nieoczekiwanych danych

W przeszłości podczas deserializacji wszelkie dane nadmiarowe lub nieoczekiwany spowodowane wyjątki zostanie wygenerowany. Z SRS w tej samej sytuacji, wszelkie dane nadmiarowe lub nieoczekiwany jest ignorowana zamiast powoduje wyjątki zostanie wygenerowany. Dzięki temu aplikacje używające nowszych wersji typu (czyli wersji zawierającej więcej pól) mogą wysyłać informacje do aplikacji, które oczekują starszych wersji tego samego typu.

W poniższym przykładzie dodatkowe dane zawarte w `CountryField` wersji 2,0 `Address` klasy są ignorowane, gdy Starsza aplikacja deserializacji nowszą wersję.

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

### <a name="tolerance-of-missing-data"></a>Tolerancja brakujących danych

Pola mogą być oznaczane jako opcjonalne przez zastosowanie <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do nich. Podczas deserializacji Jeśli brakuje danych opcjonalny mechanizm serializacji ignoruje braku i nie zgłoszony wyjątek. W ten sposób aplikacje, które oczekują starszych wersji typu, mogą wysyłać dane do aplikacji, które oczekują nowszych wersji tego samego typu.

W poniższym przykładzie przedstawiono wersję 2,0 `Address` klasy z `CountryField` polem oznaczonym jako opcjonalna. Jeśli Starsza aplikacja wysyła wersję 1 do nowszej aplikacji, która oczekuje wersji 2,0, Brak danych zostanie zignorowany.

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
  
### <a name="serialization-callbacks"></a>Wywołania zwrotne serializacji

Serializacja wywołania zwrotne są mechanizm udostępniająca punkty zaczepienia z procesem serializacji/deserializacji w cztery punkty.

|Atrybut|Gdy jest wywoływana metoda skojarzone|Typowym zastosowaniem|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Przed deserializacji.\*|Zainicjuj wartości domyślne dla pola opcjonalne.|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Po deserializacji.|Usuń zawartość wszystkich innych pól w oparciu o wartości pola opcjonalne.|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Przed serializacji.|Przygotowanie do serializacji. Na przykład utwórz opcjonalne struktury danych.|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Po serializacji.|Rejestrowanie zdarzeń serializacji.|

 \*To wywołanie zwrotne jest wywoływane przed konstruktorem deserializacji, jeśli taki istnieje.

#### <a name="using-callbacks"></a>Używanie wywołań zwrotnych

Aby użyć wywołania zwrotnego, należy zastosować odpowiedni atrybut do metody, która akceptuje <xref:System.Runtime.Serialization.StreamingContext> parametr. Może być oznaczony tylko jednej metody na klasy z każdym z tych atrybutów. Przykład:

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

Przeznaczeniem z tych metod jest przechowywania wersji. Podczas deserializacji to opcjonalne pole może nie być poprawnie zainicjować w przypadku braku danych dla tego pola. Można to naprawić, tworząc metodę, która przypisuje poprawną wartość, a następnie stosując do metody atrybut **OnDeserializingAttribute** lub **OnDeserializedAttribute** .

Poniższy przykład przedstawia metodę w kontekście typu. Jeśli wcześniejsza wersja aplikacji wysyła wystąpienie `Address` klasy do nowszej wersji aplikacji, Brak danych `CountryField` pola. Jednak po deserializacji pole zostanie ustawione na wartość domyślną "Japonia".

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
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
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a>Właściwość VersionAdded

**OptionalFieldAttribute** ma właściwość **VersionAdded** . W wersji 2,0 .NET Framework nie jest to używane. Należy jednak odpowiednio ustawić tę właściwość, aby upewnić się, że typ będzie zgodny z przyszłymi aparatami serializacji.

Właściwość wskazuje, której wersji dodano pole danego typu. Powinien być zwiększany o dokładnie jeden (od 2) za każdym razem, gdy typ jest modyfikowany, jak pokazano w następującym przykładzie:

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

Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, ponieważ wymagana jest nieco innej klasy w serwera i klienta. <xref:System.Runtime.Serialization.SerializationBinder>jest klasą abstrakcyjną służącą do kontrolowania rzeczywistych typów używanych podczas serializacji i deserializacji. Aby użyć tej klasy, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody. Aby uzyskać więcej informacji, zobacz [Kontrolowanie serializacji i deserializacji z pomocą elementu SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).

## <a name="best-practices"></a>Najlepsze rozwiązania

W celu zapewnienia zachowania właściwej wersji, modyfikując typu od wersji należy wykonać następujące czynności:

- Nigdy nie należy usunąć pole serializacji.
- Nigdy nie stosuj <xref:System.NonSerializedAttribute> atrybutu do pola, jeśli atrybut nie został zastosowany do pola w poprzedniej wersji.
- Nigdy nie można zmienić nazwy lub typu serializacji pola.
- Podczas dodawania nowego serializowanego pola, zastosuj atrybut **OptionalFieldAttribute** .
- Podczas usuwania atrybutu **nieserializowanego** z pola (którego nie można serializować w poprzedniej wersji), należy zastosować atrybut **OptionalFieldAttribute** .
- Dla wszystkich pól opcjonalnych Ustaw zrozumiałe wartości domyślne przy użyciu wywołań zwrotnych serializacji, chyba że wartości 0 lub **null** , ponieważ wartości domyślne są akceptowalne.

W celu zapewnienia, że typem będzie zgodna z aparatów przyszłych serializacji, postępuj zgodnie z tymi wytycznymi dotyczącymi:

- Zawsze należy prawidłowo ustawić właściwość **VersionAdded** atrybutu **OptionalFieldAttribute** .
- Unikaj rozgałęziony przechowywania wersji.

## <a name="see-also"></a>Zobacz też

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [Serializacja binarna](binary-serialization.md)
