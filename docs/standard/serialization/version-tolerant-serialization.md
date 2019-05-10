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
ms.openlocfilehash: a61fa5a3f87c534574d7265dfdc16365c0afbbe0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644853"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="e34b0-102">Serializacja z tolerancją wersji</span><span class="sxs-lookup"><span data-stu-id="e34b0-102">Version tolerant serialization</span></span>
<span data-ttu-id="e34b0-103">W wersji 1.0 i 1.1 programu .NET Framework tworzenie serializacji typów, które mogą być ponownie używane z jednej wersji aplikacji do następnego był problemy.</span><span class="sxs-lookup"><span data-stu-id="e34b0-103">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="e34b0-104">Jeśli typ został zmodyfikowany przez dodanie pola dodatkowe, wystąpi następujących problemów:</span><span class="sxs-lookup"><span data-stu-id="e34b0-104">If a type was modified by adding extra fields, the following problems would occur:</span></span>  
  
- <span data-ttu-id="e34b0-105">Starsze wersje aplikacji będzie zgłaszają wyjątki po pytania do nowych wersji stary typ do deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-105">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>  
  
- <span data-ttu-id="e34b0-106">Nowsze wersje aplikacji będzie zgłaszają wyjątki, gdy podczas deserializacji starszych wersji typu z brakujących danych.</span><span class="sxs-lookup"><span data-stu-id="e34b0-106">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>  
  
 <span data-ttu-id="e34b0-107">Wersja na uszkodzenia serializacji (SRS) to zestaw funkcje wprowadzone w programie .NET Framework 2.0, który ułatwia, wraz z upływem czasu, aby zmodyfikować typów możliwych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-107">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="e34b0-108">W szczególności funkcje SRS są włączone dla klasy, do której <xref:System.SerializableAttribute> zastosowano atrybut, w tym typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="e34b0-108">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="e34b0-109">SRS sprawia, że można dodać nowe pola do tych klas bez przerywania zgodność z innymi wersjami tego typu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-109">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="e34b0-110">Pracy przykładowej aplikacji, zobacz [wersja na uszkodzenia przykład technologii serializacji](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="e34b0-110">For a working sample application, see [Version Tolerant Serialization Technology Sample](../../../docs/standard/serialization/version-tolerant-serialization-technology-sample.md).</span></span>  
  
 <span data-ttu-id="e34b0-111">Funkcje SRS są włączone, korzystając z <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="e34b0-111">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="e34b0-112">Ponadto wszystkie funkcje, z wyjątkiem tolerancja nadmiarowe dane są również włączone podczas korzystania z <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="e34b0-112">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="e34b0-113">Aby uzyskać więcej informacji o korzystaniu z tych klas do serializacji, zobacz [serializacji binarnej](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e34b0-113">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>  
  
[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="e34b0-114">Lista funkcji</span><span class="sxs-lookup"><span data-stu-id="e34b0-114">Feature list</span></span>  
 <span data-ttu-id="e34b0-115">Zestaw funkcji obejmuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e34b0-115">The set of features includes the following:</span></span>  
  
- <span data-ttu-id="e34b0-116">Tolerancja danych zewnętrznych lub nieoczekiwany.</span><span class="sxs-lookup"><span data-stu-id="e34b0-116">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="e34b0-117">Dzięki temu nowszych wersji typu wysyłać dane do starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-117">This enables newer versions of the type to send data to older versions.</span></span>  
  
- <span data-ttu-id="e34b0-118">Tolerancja brakujących opcjonalnymi danymi.</span><span class="sxs-lookup"><span data-stu-id="e34b0-118">Tolerance of missing optional data.</span></span> <span data-ttu-id="e34b0-119">Dzięki temu starszych wersji wysyłać dane do nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-119">This enables older versions to send data to newer versions.</span></span>  
  
- <span data-ttu-id="e34b0-120">Serializacja wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-120">Serialization callbacks.</span></span> <span data-ttu-id="e34b0-121">Dzięki temu inteligentną domyślne ustawienie wartości w przypadkach, gdy jest Brak danych.</span><span class="sxs-lookup"><span data-stu-id="e34b0-121">This enables intelligent default value setting in cases where data is missing.</span></span>  
  
 <span data-ttu-id="e34b0-122">Ponadto to funkcja do deklarowania, gdy zostało dodane nowe pole opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-122">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="e34b0-123">Jest to <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> właściwości <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-123">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>  
  
 <span data-ttu-id="e34b0-124">Te funkcje opisano szczegółowo poniżej.</span><span class="sxs-lookup"><span data-stu-id="e34b0-124">These features are discussed in greater detail below.</span></span>  
  
## <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="e34b0-125">Tolerancja nadmiarowe lub nieoczekiwany danych</span><span class="sxs-lookup"><span data-stu-id="e34b0-125">Tolerance of extraneous or unexpected data</span></span>  
 <span data-ttu-id="e34b0-126">W przeszłości podczas deserializacji wszelkie dane nadmiarowe lub nieoczekiwany spowodowane wyjątki zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e34b0-126">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="e34b0-127">Z SRS w tej samej sytuacji, wszelkie dane nadmiarowe lub nieoczekiwany jest ignorowana zamiast powoduje wyjątki zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e34b0-127">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="e34b0-128">Umożliwia to aplikacji, które używają nowszych wersji typu (czyli wersji, który zawiera więcej pól) do wysyłania informacji do aplikacji, które oczekują starszych wersji tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-128">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>  
  
 <span data-ttu-id="e34b0-129">W poniższym przykładzie dodatkowe dane zawarte w `CountryField` w wersji 2.0 programu `Address` klasy jest ignorowana, gdy starszych aplikacji deserializuje nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-129">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>  
  
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
  
## <a name="tolerance-of-missing-data"></a><span data-ttu-id="e34b0-130">Tolerancja Brak danych</span><span class="sxs-lookup"><span data-stu-id="e34b0-130">Tolerance of missing data</span></span>  
 <span data-ttu-id="e34b0-131">Pola może być oznaczona jako opcjonalną przez zastosowanie <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do nich.</span><span class="sxs-lookup"><span data-stu-id="e34b0-131">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="e34b0-132">Podczas deserializacji Jeśli brakuje danych opcjonalny mechanizm serializacji ignoruje braku i nie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e34b0-132">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="e34b0-133">W związku z tym aplikacje, które oczekują starszych wersji typu mogą wysyłać dane do aplikacji, które oczekują nowszych wersji tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-133">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>  
  
 <span data-ttu-id="e34b0-134">W poniższym przykładzie pokazano wersję 2.0 `Address` klasy `CountryField` pole oznaczone jako opcjonalną.</span><span class="sxs-lookup"><span data-stu-id="e34b0-134">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="e34b0-135">Jeśli starszych aplikacji w wersji 1 są wysyłane do nowszych aplikacji, który oczekuje w wersji 2.0, Brak danych jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="e34b0-135">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>  
  
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
  
## <a name="serialization-callbacks"></a><span data-ttu-id="e34b0-136">Serializacja wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="e34b0-136">Serialization callbacks</span></span>  
 <span data-ttu-id="e34b0-137">Serializacja wywołania zwrotne są mechanizm udostępniająca punkty zaczepienia z procesem serializacji/deserializacji w cztery punkty.</span><span class="sxs-lookup"><span data-stu-id="e34b0-137">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>  
  
|<span data-ttu-id="e34b0-138">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e34b0-138">Attribute</span></span>|<span data-ttu-id="e34b0-139">Gdy jest wywoływana metoda skojarzone</span><span class="sxs-lookup"><span data-stu-id="e34b0-139">When the Associated Method is Called</span></span>|<span data-ttu-id="e34b0-140">Typowym zastosowaniem</span><span class="sxs-lookup"><span data-stu-id="e34b0-140">Typical Use</span></span>|  
|---------------|------------------------------------------|-----------------|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="e34b0-141">Przed deserialization.\*</span><span class="sxs-lookup"><span data-stu-id="e34b0-141">Before deserialization.\*</span></span>|<span data-ttu-id="e34b0-142">Zainicjuj wartości domyślne dla pola opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-142">Initialize default values for optional fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="e34b0-143">Po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-143">After deserialization.</span></span>|<span data-ttu-id="e34b0-144">Usuń zawartość wszystkich innych pól w oparciu o wartości pola opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-144">Fix optional field values based on contents of other fields.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="e34b0-145">Przed serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-145">Before serialization.</span></span>|<span data-ttu-id="e34b0-146">Przygotowanie do serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-146">Prepare for serialization.</span></span> <span data-ttu-id="e34b0-147">Na przykład można utworzyć struktury danych opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-147">For example, create optional data structures.</span></span>|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="e34b0-148">Po serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-148">After serialization.</span></span>|<span data-ttu-id="e34b0-149">Rejestrowanie zdarzeń serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-149">Log serialization events.</span></span>|  
  
 <span data-ttu-id="e34b0-150">\* To wywołanie zwrotne jest wywoływana przed w Konstruktorze deserializacji, jeśli jest obecna.</span><span class="sxs-lookup"><span data-stu-id="e34b0-150">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>  
  
### <a name="using-callbacks"></a><span data-ttu-id="e34b0-151">Za pomocą wywołania zwrotne</span><span class="sxs-lookup"><span data-stu-id="e34b0-151">Using callbacks</span></span>  
 <span data-ttu-id="e34b0-152">Aby korzystać z wywołań zwrotnych, zastosowanie odpowiedniego atrybutu do metody, która akceptuje <xref:System.Runtime.Serialization.StreamingContext> parametru.</span><span class="sxs-lookup"><span data-stu-id="e34b0-152">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="e34b0-153">Może być oznaczony tylko jednej metody na klasy z każdym z tych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e34b0-153">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="e34b0-154">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e34b0-154">For example:</span></span>  
  
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
  
 <span data-ttu-id="e34b0-155">Przeznaczeniem z tych metod jest przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-155">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="e34b0-156">Podczas deserializacji to opcjonalne pole może nie być poprawnie zainicjować w przypadku braku danych dla tego pola.</span><span class="sxs-lookup"><span data-stu-id="e34b0-156">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="e34b0-157">Ten problem można rozwiązać przez tworzenie metody, która przypisuje poprawnej wartości, a następnie stosowanie **OnDeserializingAttribute** lub **OnDeserializedAttribute** atrybutu do metody.</span><span class="sxs-lookup"><span data-stu-id="e34b0-157">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>  
  
 <span data-ttu-id="e34b0-158">Poniższy przykład przedstawia metodę w kontekście określonego typu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-158">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="e34b0-159">Jeśli starszą wersję aplikacji wysyła wystąpienia `Address` klasy do nowszej wersji aplikacji, `CountryField` danych pola będą niedostępne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-159">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="e34b0-160">Ale po deserializacji, pola zostanie ustawiona na wartość domyślną "Japonia".</span><span class="sxs-lookup"><span data-stu-id="e34b0-160">But after deserialization, the field will be set to a default value "Japan."</span></span>  
  
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
  
## <a name="the-versionadded-property"></a><span data-ttu-id="e34b0-161">Właściwość VersionAdded</span><span class="sxs-lookup"><span data-stu-id="e34b0-161">The VersionAdded property</span></span>  
 <span data-ttu-id="e34b0-162">**OptionalFieldAttribute** ma **VersionAdded** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e34b0-162">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="e34b0-163">W wersji 2.0 programu .NET Framework, to nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="e34b0-163">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="e34b0-164">Jest ważne, aby poprawnie ustawić tę właściwość, aby upewnić się, że typ będzie zgodna z aparatów przyszłych serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-164">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>  
  
 <span data-ttu-id="e34b0-165">Właściwość wskazuje, której wersji dodano pole danego typu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-165">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="e34b0-166">Powinien być zwiększane o dokładnie jeden (rozpoczyna się od 2) za każdym razem, gdy typ został zmodyfikowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e34b0-166">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>  
  
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
  
## <a name="serializationbinder"></a><span data-ttu-id="e34b0-167">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="e34b0-167">SerializationBinder</span></span>  
 <span data-ttu-id="e34b0-168">Niektórzy użytkownicy może być konieczne do kontrolowania której klasy do serializacji i deserializacji, ponieważ wymagana jest nieco innej klasy w serwera i klienta.</span><span class="sxs-lookup"><span data-stu-id="e34b0-168">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="e34b0-169"><xref:System.Runtime.Serialization.SerializationBinder> Klasa abstrakcyjna służy do kontroli rzeczywiste typy używane podczas serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-169"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span>  <span data-ttu-id="e34b0-170">Aby użyć tej klasy, należy wyprowadzić klasę z <xref:System.Runtime.Serialization.SerializationBinder> i zastąpić <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> i <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e34b0-170">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="e34b0-171">Aby uzyskać więcej informacji, zobacz [kontrolowanie serializacji i deserializacji za pomocą elementu SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="e34b0-171">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../../docs/framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="e34b0-172">Najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="e34b0-172">Best practices</span></span>  
 <span data-ttu-id="e34b0-173">W celu zapewnienia zachowania właściwej wersji, modyfikując typu od wersji należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e34b0-173">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>  
  
- <span data-ttu-id="e34b0-174">Nigdy nie należy usunąć pole serializacji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-174">Never remove a serialized field.</span></span>  
  
- <span data-ttu-id="e34b0-175">Nigdy nie stosuj <xref:System.NonSerializedAttribute> atrybutu do pola, jeśli ten atrybut nie została zastosowana do pola w poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-175">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>  
  
- <span data-ttu-id="e34b0-176">Nigdy nie można zmienić nazwy lub typu serializacji pola.</span><span class="sxs-lookup"><span data-stu-id="e34b0-176">Never change the name or the type of a serialized field.</span></span>  
  
- <span data-ttu-id="e34b0-177">Podczas dodawania nowe pole serializacji, zastosuj **OptionalFieldAttribute** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-177">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>  
  
- <span data-ttu-id="e34b0-178">Podczas usuwania **NonSerializedAttribute** atrybutu z polem (które nie były możliwe do serializacji w poprzedniej wersji), zastosuj **OptionalFieldAttribute** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e34b0-178">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>  
  
- <span data-ttu-id="e34b0-179">Dla wszystkich pól opcjonalne ustawienia zrozumiałe domyślne, o których przy użyciu wywołania zwrotne serializacji, chyba że 0 lub **null** jako akceptowane są wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="e34b0-179">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>  
  
 <span data-ttu-id="e34b0-180">W celu zapewnienia, że typem będzie zgodna z aparatów przyszłych serializacji, postępuj zgodnie z tymi wytycznymi dotyczącymi:</span><span class="sxs-lookup"><span data-stu-id="e34b0-180">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>  
  
- <span data-ttu-id="e34b0-181">Zawsze wartość **VersionAdded** właściwość **OptionalFieldAttribute** atrybutu prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="e34b0-181">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>  
  
- <span data-ttu-id="e34b0-182">Unikaj rozgałęziony przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="e34b0-182">Avoid branched versioning.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34b0-183">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e34b0-183">See also</span></span>

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
- [<span data-ttu-id="e34b0-184">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="e34b0-184">Binary Serialization</span></span>](binary-serialization.md)
