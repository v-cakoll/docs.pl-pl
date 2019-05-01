---
title: Serializacja z tolerancją wersji
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
ms.openlocfilehash: c899cfe1015a25adc25fc28ee84d0a37a397defe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028255"
---
# <a name="version-tolerant-serialization"></a>Serializacja z tolerancją wersji
W wersji 1.0 i 1.1 programu .NET Framework tworzenie serializacji typów, które mogą być ponownie używane z jednej wersji aplikacji do następnego był problemy. Jeśli typ został zmodyfikowany przez dodanie pola dodatkowe, wystąpi następujących problemów:  
  
- Starsze wersje aplikacji będzie zgłaszają wyjątki po pytania do nowych wersji stary typ do deserializacji.  
  
- Nowsze wersje aplikacji będzie zgłaszają wyjątki, gdy podczas deserializacji starszych wersji typu z brakujących danych.  
  
 Wersja na uszkodzenia serializacji (SRS) to zestaw funkcje wprowadzone w programie .NET Framework 2.0, który ułatwia, wraz z upływem czasu, aby zmodyfikować typów możliwych do serializacji. W szczególności funkcje SRS są włączone dla klasy, do której <xref:System.SerializableAttribute> zastosowano atrybut, w tym typów ogólnych. SRS sprawia, że można dodać nowe pola do tych klas bez przerywania zgodność z innymi wersjami tego typu. Pracy przykładowej aplikacji, zobacz [wersja na uszkodzenia przykład technologii serializacji](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).  
  
 Funkcje SRS są włączone, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Ponadto wszystkie funkcje, z wyjątkiem tolerancja nadmiarowe dane są również włączone podczas korzystania z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Aby uzyskać więcej informacji o korzystaniu z tych klas do serializacji, zobacz [serializacji binarnej](binary-serialization.md).  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a>Lista funkcji  
 Zestaw funkcji obejmuje następujące czynności:  
  
- Tolerancja danych zewnętrznych lub nieoczekiwany. Dzięki temu nowszych wersji typu wysyłać dane do starszych wersji.  
  
- Tolerancja brakujących opcjonalnymi danymi. Dzięki temu starszych wersji wysyłać dane do nowszych wersji.  
  
- Serializacja wywołania zwrotne. Dzięki temu inteligentną domyślne ustawienie wartości w przypadkach, gdy jest Brak danych.  
  
 Ponadto to funkcja do deklarowania, gdy zostało dodane nowe pole opcjonalne. Jest to <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> właściwości <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu.  
  
 Te funkcje opisano szczegółowo poniżej.  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a>Tolerancja nadmiarowe lub nieoczekiwany danych  
 W przeszłości podczas deserializacji wszelkie dane nadmiarowe lub nieoczekiwany spowodowane wyjątki zostanie wygenerowany. Z SRS w tej samej sytuacji, wszelkie dane nadmiarowe lub nieoczekiwany jest ignorowana zamiast powoduje wyjątki zostanie wygenerowany. Umożliwia to aplikacji, które używają nowszych wersji typu (czyli wersji, który zawiera więcej pól) do wysyłania informacji do aplikacji, które oczekują starszych wersji tego samego typu.  
  
 W poniższym przykładzie dodatkowe dane zawarte w `CountryField` w wersji 2.0 programu `Address` klasy jest ignorowana, gdy starszych aplikacji deserializuje nowszej wersji.  
  
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
  
## <a name="tolerance-of-missing-data"></a>Tolerancja Brak danych  
 Pola może być oznaczona jako opcjonalną przez zastosowanie <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do nich. Podczas deserializacji Jeśli brakuje danych opcjonalny mechanizm serializacji ignoruje braku i nie zgłoszony wyjątek. W związku z tym aplikacje, które oczekują starszych wersji typu mogą wysyłać dane do aplikacji, które oczekują nowszych wersji tego samego typu.  
  
 W poniższym przykładzie pokazano wersję 2.0 `Address` klasy `CountryField` pole oznaczone jako opcjonalną. Jeśli starszych aplikacji w wersji 1 są wysyłane do nowszych aplikacji, który oczekuje w wersji 2.0, Brak danych jest ignorowana.  
  
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
  
## <a name="serialization-callbacks"></a>Serializacja wywołania zwrotne  
 Serializacja wywołania zwrotne są mechanizm udostępniająca punkty zaczepienia z procesem serializacji/deserializacji w cztery punkty.  
  
|Atrybut|Gdy jest wywoływana metoda skojarzone|Typowym zastosowaniem|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Przed deserialization.*|Zainicjuj wartości domyślne dla pola opcjonalne.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Po deserializacji.|Usuń zawartość wszystkich innych pól w oparciu o wartości pola opcjonalne.|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Przed serializacji.|Przygotowanie do serializacji. Na przykład można utworzyć struktury danych opcjonalne.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Po serializacji.|Rejestrowanie zdarzeń serializacji.|  
  
 \* To wywołanie zwrotne jest wywoływana przed w Konstruktorze deserializacji, jeśli jest obecna.  
  
### <a name="using-callbacks"></a>Za pomocą wywołania zwrotne  
 Aby korzystać z wywołań zwrotnych, zastosowanie odpowiedniego atrybutu do metody, która akceptuje <xref:System.Runtime.Serialization.StreamingContext> parametru. Może być oznaczony tylko jednej metody na klasy z każdym z tych atrybutów. Na przykład:  
  
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
  
 Przeznaczeniem z tych metod jest przechowywania wersji. Podczas deserializacji to opcjonalne pole może nie być poprawnie zainicjować w przypadku braku danych dla tego pola. Ten problem można rozwiązać przez tworzenie metody, która przypisuje poprawnej wartości, a następnie stosowanie **OnDeserializingAttribute** lub **OnDeserializedAttribute** atrybutu do metody.  
  
 Poniższy przykład przedstawia metodę w kontekście określonego typu. Jeśli starszą wersję aplikacji wysyła wystąpienia `Address` klasy do nowszej wersji aplikacji, `CountryField` danych pola będą niedostępne. Ale po deserializacji, pola zostanie ustawiona na wartość domyślną "Japonia".  
  
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
 **OptionalFieldAttribute** ma **VersionAdded** właściwości. W wersji 2.0 programu .NET Framework, to nie jest używany. Jest ważne, aby poprawnie ustawić tę właściwość, aby upewnić się, że typ będzie zgodna z aparatów przyszłych serializacji.  
  
 Właściwość wskazuje, której wersji dodano pole danego typu. Powinien być zwiększane o dokładnie jeden (rozpoczyna się od 2) za każdym razem, gdy typ został zmodyfikowany, jak pokazano w poniższym przykładzie:  
  
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
 Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, ponieważ wymagana jest nieco innej klasy w serwera i klienta. <xref:System.Runtime.Serialization.SerializationBinder> Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji.  Aby użyć tej klasy, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody. Aby uzyskać więcej informacji, zobacz [kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
 W celu zapewnienia zachowania właściwej wersji, modyfikując typu od wersji należy wykonać następujące czynności:  
  
- Nigdy nie należy usunąć pole serializacji.  
  
- Nigdy nie stosuj <xref:System.NonSerializedAttribute> atrybutu do pola, jeśli ten atrybut nie została zastosowana do pola w poprzedniej wersji.  
  
- Nigdy nie można zmienić nazwy lub typu serializacji pola.  
  
- Podczas dodawania nowe pole serializacji, zastosuj **OptionalFieldAttribute** atrybutu.  
  
- Podczas usuwania **NonSerializedAttribute** atrybutu z polem (które nie były możliwe do serializacji w poprzedniej wersji), zastosuj **OptionalFieldAttribute** atrybutu.  
  
- Dla wszystkich pól opcjonalne ustawienia zrozumiałe domyślne, o których przy użyciu wywołania zwrotne serializacji, chyba że 0 lub **null** jako akceptowane są wartości domyślne.  
  
 W celu zapewnienia, że typem będzie zgodna z aparatów przyszłych serializacji, postępuj zgodnie z tymi wytycznymi dotyczącymi:  
  
- Zawsze wartość **VersionAdded** właściwość **OptionalFieldAttribute** atrybutu prawidłowo.  
  
- Unikaj rozgałęziony przechowywania wersji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [Serializacja binarna](binary-serialization.md)
