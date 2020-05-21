---
title: Serializacja odporna na wersje
description: .NET Framework 2,0 wprowadza serializacji odpornej na wersje, zestaw funkcji, które ułatwiają Modyfikowanie typów możliwych do serializacji.
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
ms.openlocfilehash: afc822e1f8873bac069f6634fdf1d4665d392e69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762594"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="6c21d-103">Serializacja odporna na wersje</span><span class="sxs-lookup"><span data-stu-id="6c21d-103">Version tolerant serialization</span></span>

<span data-ttu-id="6c21d-104">W wersji 1,0 i 1,1 .NET Framework, tworzenie możliwych do przetworzenia typów, które mogą być wielokrotnego użytku z jednej wersji aplikacji do następnej była problematyczne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="6c21d-105">Jeśli typ został zmodyfikowany przez dodanie pola dodatkowe, wystąpi następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="6c21d-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="6c21d-106">Starsze wersje aplikacji mogą generować wyjątki, gdy zostanie wyświetlony monit o deserializacja nowych wersji starego typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="6c21d-107">Nowsze wersje aplikacji spowodują wygenerowanie wyjątków podczas deserializacji starszych wersji typu z brakującymi danymi.</span><span class="sxs-lookup"><span data-stu-id="6c21d-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="6c21d-108">Wersja na uszkodzenia serializacji (SRS) to zestaw funkcje wprowadzone w programie .NET Framework 2.0, który ułatwia, wraz z upływem czasu, aby zmodyfikować typów możliwych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="6c21d-109">W szczególności funkcje SRS są włączone dla klas, do których <xref:System.SerializableAttribute> zastosowano atrybut, w tym typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="6c21d-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="6c21d-110">SRS sprawia, że można dodać nowe pola do tych klas bez przerywania zgodność z innymi wersjami tego typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="6c21d-111">Aby uzyskać działającą przykładową aplikację, zobacz [przykład technologii serializacji odpornej na wersje](basic-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="6c21d-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="6c21d-112">Funkcje SRS są włączone, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="6c21d-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="6c21d-113">Ponadto wszystkie funkcje, z wyjątkiem tolerancja nadmiarowe dane są również włączone podczas korzystania z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="6c21d-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="6c21d-114">Aby uzyskać więcej informacji o używaniu tych klas do serializacji, zobacz [Serializacja binarna](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="6c21d-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="6c21d-115">Lista funkcji</span><span class="sxs-lookup"><span data-stu-id="6c21d-115">Feature list</span></span>

<span data-ttu-id="6c21d-116">Zestaw funkcji obejmuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6c21d-116">The set of features includes the following:</span></span>

- <span data-ttu-id="6c21d-117">Tolerancja danych zewnętrznych lub nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="6c21d-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="6c21d-118">Dzięki temu nowszych wersji typu wysyłać dane do starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="6c21d-119">Tolerancja brakujących opcjonalnymi danymi.</span><span class="sxs-lookup"><span data-stu-id="6c21d-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="6c21d-120">Dzięki temu starszych wersji wysyłać dane do nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="6c21d-121">Serializacja wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-121">Serialization callbacks.</span></span> <span data-ttu-id="6c21d-122">Dzięki temu inteligentną domyślne ustawienie wartości w przypadkach, gdy jest Brak danych.</span><span class="sxs-lookup"><span data-stu-id="6c21d-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="6c21d-123">Ponadto to funkcja do deklarowania, gdy zostało dodane nowe pole opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="6c21d-124">Jest to <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> właściwości <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="6c21d-125">Te funkcje zostały omówione bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="6c21d-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="6c21d-126">Tolerancja niektórych lub nieoczekiwanych danych</span><span class="sxs-lookup"><span data-stu-id="6c21d-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="6c21d-127">W przeszłości podczas deserializacji wszelkie dane nadmiarowe lub nieoczekiwany spowodowane wyjątki zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6c21d-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="6c21d-128">Z SRS w tej samej sytuacji, wszelkie dane nadmiarowe lub nieoczekiwany jest ignorowana zamiast powoduje wyjątki zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6c21d-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="6c21d-129">Dzięki temu aplikacje używające nowszych wersji typu (czyli wersji zawierającej więcej pól) mogą wysyłać informacje do aplikacji, które oczekują starszych wersji tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="6c21d-130">W poniższym przykładzie dodatkowe dane zawarte w `CountryField` wersji 2,0 `Address` klasy są ignorowane, gdy Starsza aplikacja deserializacji nowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="6c21d-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

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

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="6c21d-131">Tolerancja brakujących danych</span><span class="sxs-lookup"><span data-stu-id="6c21d-131">Tolerance of missing data</span></span>

<span data-ttu-id="6c21d-132">Pola mogą być oznaczane jako opcjonalne przez zastosowanie <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do nich.</span><span class="sxs-lookup"><span data-stu-id="6c21d-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="6c21d-133">Podczas deserializacji Jeśli brakuje danych opcjonalny mechanizm serializacji ignoruje braku i nie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="6c21d-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="6c21d-134">W ten sposób aplikacje, które oczekują starszych wersji typu, mogą wysyłać dane do aplikacji, które oczekują nowszych wersji tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="6c21d-135">W poniższym przykładzie przedstawiono wersję 2,0 `Address` klasy z `CountryField` polem oznaczonym jako opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="6c21d-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="6c21d-136">Jeśli Starsza aplikacja wysyła wersję 1 do nowszej aplikacji, która oczekuje wersji 2,0, Brak danych zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="6c21d-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

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
  
### <a name="serialization-callbacks"></a><span data-ttu-id="6c21d-137">Wywołania zwrotne serializacji</span><span class="sxs-lookup"><span data-stu-id="6c21d-137">Serialization callbacks</span></span>

<span data-ttu-id="6c21d-138">Serializacja wywołania zwrotne są mechanizm udostępniająca punkty zaczepienia z procesem serializacji/deserializacji w cztery punkty.</span><span class="sxs-lookup"><span data-stu-id="6c21d-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="6c21d-139">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6c21d-139">Attribute</span></span>|<span data-ttu-id="6c21d-140">Gdy jest wywoływana metoda skojarzone</span><span class="sxs-lookup"><span data-stu-id="6c21d-140">When the Associated Method is Called</span></span>|<span data-ttu-id="6c21d-141">Typowym zastosowaniem</span><span class="sxs-lookup"><span data-stu-id="6c21d-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="6c21d-142">Przed deserializacji.\*</span><span class="sxs-lookup"><span data-stu-id="6c21d-142">Before deserialization.\*</span></span>|<span data-ttu-id="6c21d-143">Zainicjuj wartości domyślne dla pola opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="6c21d-144">Po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-144">After deserialization.</span></span>|<span data-ttu-id="6c21d-145">Usuń zawartość wszystkich innych pól w oparciu o wartości pola opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="6c21d-146">Przed serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-146">Before serialization.</span></span>|<span data-ttu-id="6c21d-147">Przygotowanie do serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-147">Prepare for serialization.</span></span> <span data-ttu-id="6c21d-148">Na przykład utwórz opcjonalne struktury danych.</span><span class="sxs-lookup"><span data-stu-id="6c21d-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="6c21d-149">Po serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-149">After serialization.</span></span>|<span data-ttu-id="6c21d-150">Rejestrowanie zdarzeń serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-150">Log serialization events.</span></span>|

 <span data-ttu-id="6c21d-151">\*To wywołanie zwrotne jest wywoływane przed konstruktorem deserializacji, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="6c21d-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="6c21d-152">Używanie wywołań zwrotnych</span><span class="sxs-lookup"><span data-stu-id="6c21d-152">Using callbacks</span></span>

<span data-ttu-id="6c21d-153">Aby użyć wywołania zwrotnego, należy zastosować odpowiedni atrybut do metody, która akceptuje <xref:System.Runtime.Serialization.StreamingContext> parametr.</span><span class="sxs-lookup"><span data-stu-id="6c21d-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="6c21d-154">Może być oznaczony tylko jednej metody na klasy z każdym z tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6c21d-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="6c21d-155">Przykład:</span><span class="sxs-lookup"><span data-stu-id="6c21d-155">For example:</span></span>

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

<span data-ttu-id="6c21d-156">Przeznaczeniem z tych metod jest przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="6c21d-157">Podczas deserializacji to opcjonalne pole może nie być poprawnie zainicjować w przypadku braku danych dla tego pola.</span><span class="sxs-lookup"><span data-stu-id="6c21d-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="6c21d-158">Można to naprawić, tworząc metodę, która przypisuje poprawną wartość, a następnie stosując do metody atrybut **OnDeserializingAttribute** lub **OnDeserializedAttribute** .</span><span class="sxs-lookup"><span data-stu-id="6c21d-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="6c21d-159">Poniższy przykład przedstawia metodę w kontekście typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="6c21d-160">Jeśli wcześniejsza wersja aplikacji wysyła wystąpienie `Address` klasy do nowszej wersji aplikacji, `CountryField` Brak danych pola.</span><span class="sxs-lookup"><span data-stu-id="6c21d-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="6c21d-161">Jednak po deserializacji pole zostanie ustawione na wartość domyślną "Japonia".</span><span class="sxs-lookup"><span data-stu-id="6c21d-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

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

## <a name="the-versionadded-property"></a><span data-ttu-id="6c21d-162">Właściwość VersionAdded</span><span class="sxs-lookup"><span data-stu-id="6c21d-162">The VersionAdded property</span></span>

<span data-ttu-id="6c21d-163">**OptionalFieldAttribute** ma właściwość **VersionAdded** .</span><span class="sxs-lookup"><span data-stu-id="6c21d-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="6c21d-164">W wersji 2,0 .NET Framework nie jest to używane.</span><span class="sxs-lookup"><span data-stu-id="6c21d-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="6c21d-165">Należy jednak odpowiednio ustawić tę właściwość, aby upewnić się, że typ będzie zgodny z przyszłymi aparatami serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="6c21d-166">Właściwość wskazuje, której wersji dodano pole danego typu.</span><span class="sxs-lookup"><span data-stu-id="6c21d-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="6c21d-167">Powinien być zwiększany o dokładnie jeden (od 2) za każdym razem, gdy typ jest modyfikowany, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6c21d-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

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

## <a name="serializationbinder"></a><span data-ttu-id="6c21d-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="6c21d-168">SerializationBinder</span></span>

<span data-ttu-id="6c21d-169">Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, ponieważ wymagana jest nieco innej klasy w serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="6c21d-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="6c21d-170"><xref:System.Runtime.Serialization.SerializationBinder>jest klasą abstrakcyjną służącą do kontrolowania rzeczywistych typów używanych podczas serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="6c21d-171">Aby użyć tej klasy, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6c21d-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="6c21d-172">Aby uzyskać więcej informacji, zobacz [Kontrolowanie serializacji i deserializacji z pomocą elementu SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="6c21d-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="6c21d-173">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6c21d-173">Best practices</span></span>

<span data-ttu-id="6c21d-174">W celu zapewnienia zachowania właściwej wersji, modyfikując typu od wersji należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6c21d-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="6c21d-175">Nigdy nie należy usunąć pole serializacji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="6c21d-176">Nigdy nie stosuj <xref:System.NonSerializedAttribute> atrybutu do pola, jeśli atrybut nie został zastosowany do pola w poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="6c21d-177">Nigdy nie można zmienić nazwy lub typu serializacji pola.</span><span class="sxs-lookup"><span data-stu-id="6c21d-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="6c21d-178">Podczas dodawania nowego serializowanego pola, zastosuj atrybut **OptionalFieldAttribute** .</span><span class="sxs-lookup"><span data-stu-id="6c21d-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="6c21d-179">Podczas usuwania atrybutu **nieserializowanego** z pola (którego nie można serializować w poprzedniej wersji), należy zastosować atrybut **OptionalFieldAttribute** .</span><span class="sxs-lookup"><span data-stu-id="6c21d-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="6c21d-180">Dla wszystkich pól opcjonalnych Ustaw zrozumiałe wartości domyślne przy użyciu wywołań zwrotnych serializacji, chyba że wartości 0 lub **null** , ponieważ wartości domyślne są akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="6c21d-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="6c21d-181">W celu zapewnienia, że typem będzie zgodna z aparatów przyszłych serializacji, postępuj zgodnie z tymi wytycznymi dotyczącymi:</span><span class="sxs-lookup"><span data-stu-id="6c21d-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="6c21d-182">Zawsze należy prawidłowo ustawić właściwość **VersionAdded** atrybutu **OptionalFieldAttribute** .</span><span class="sxs-lookup"><span data-stu-id="6c21d-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="6c21d-183">Unikaj rozgałęziony przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="6c21d-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c21d-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c21d-184">See also</span></span>

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
- [<span data-ttu-id="6c21d-185">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="6c21d-185">Binary Serialization</span></span>](binary-serialization.md)
