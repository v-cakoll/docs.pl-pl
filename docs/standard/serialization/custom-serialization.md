---
title: Serializacja niestandardowa
description: Serializacja niestandardowa kontroluje serializacji i deserializacji typu. Kontrolowanie serializacji może zapewnić zgodność serializacji.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: 1532c4eeb09e7110d0f369ec47f342256889e576
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289658"
---
# <a name="custom-serialization"></a><span data-ttu-id="fe5b1-104">Serializacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="fe5b1-104">Custom serialization</span></span>
<span data-ttu-id="fe5b1-105">Niestandardowej serializacji to proces sterowania serializacji i deserializacji obiektu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-105">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="fe5b1-106">Kontrolując serializacji, można zapewnić zgodność serializacji, która jest możliwością serializacji i deserializacji między wersjami typu bez przerywania podstawowej funkcjonalności typu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-106">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="fe5b1-107">Na przykład w pierwszej wersji typu mogą istnieć tylko dwa pola.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-107">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="fe5b1-108">W następnej wersji typu są dodawane kilka więcej pól.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-108">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="fe5b1-109">Jeszcze druga wersja aplikacji musi mieć możliwość serializacji i deserializacji obu typów.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-109">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="fe5b1-110">W następujących sekcjach opisano kontrola serializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-110">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="fe5b1-111">W wersjach wcześniejszych niż .NET Framework 4,0 Serializacja niestandardowych danych użytkownika w częściowo zaufanym zestawie została zrealizowana przy użyciu GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-111">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="fe5b1-112">Począwszy od wersji 4.0, metoda jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, co uniemożliwia wykonanie w częściowo zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-112">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="fe5b1-113">Aby obejść ten warunek, zaimplementuj <xref:System.Runtime.Serialization.ISafeSerializationData> interfejs.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-113">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="fe5b1-114">Uruchamianie metod niestandardowych w trakcie serializacji i po nim</span><span class="sxs-lookup"><span data-stu-id="fe5b1-114">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="fe5b1-115">Najlepszym rozwiązaniem i najprostszym sposobem (wprowadzonym w wersji 2,0 .NET Framework) jest stosowanie następujących atrybutów do metod, które są używane do poprawiania danych podczas serializacji i po nim:</span><span class="sxs-lookup"><span data-stu-id="fe5b1-115">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="fe5b1-116">Te atrybuty zezwalać na typ do korzystania z jednej z lub wszystkie cztery fazy procesy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-116">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="fe5b1-117">Atrybuty określają metody, które powinny być używane w fazie każdego typu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-117">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="fe5b1-118">Metody nie uzyskać dostępu do strumienia serializacji, ale umożliwiają zamiast tego można zmieniać przed i po serializacji, lub przed i po deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-118">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="fe5b1-119">Atrybuty mogą być stosowane na wszystkich poziomach hierarchii dziedziczenia typu, a każda metoda jest wywoływana w hierarchii od bazy do najbardziej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-119">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="fe5b1-120">Ten mechanizm pozwala uniknąć złożoności i wszelkich powstających problemów związanych z implementacją <xref:System.Runtime.Serialization.ISerializable> interfejsu przez nadanie odpowiedzialności za serializację i deserializacja do najbardziej pochodnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-120">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="fe5b1-121">Ponadto ten mechanizm pozwala elementy formatujące do ignorowania populacji pola i pobieranie ze strumienia serializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-121">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="fe5b1-122">Aby uzyskać szczegółowe informacje i przykłady kontrolowania serializacji i deserializacji, kliknij dowolne z poprzednich linków.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-122">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="fe5b1-123">Ponadto podczas dodawania nowego pola do istniejącego typu możliwego do serializacji należy zastosować <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybut do pola.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-123">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="fe5b1-124"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje braku pola podczas przetwarzania strumienia, w którym brakuje nowe pole.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-124">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="fe5b1-125">Implementowanie interfejsu ISerializable</span><span class="sxs-lookup"><span data-stu-id="fe5b1-125">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="fe5b1-126">Innym sposobem na kontrolowanie serializacji jest osiągnięcie przez implementację <xref:System.Runtime.Serialization.ISerializable> interfejsu w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-126">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="fe5b1-127">Należy jednak pamiętać, że metoda w poprzedniej sekcji zastępuje tę metodę w celu sterowania serializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-127">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="fe5b1-128">Ponadto nie należy używać serializacji domyślnej dla klasy, która jest oznaczona atrybutem [Serializable](xref:System.SerializableAttribute) i ma deklaratywne lub bezwzględne zabezpieczenia na poziomie klasy lub w konstruktorach.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-128">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="fe5b1-129">Zamiast tego te klasy powinny zawsze implementować <xref:System.Runtime.Serialization.ISerializable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-129">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="fe5b1-130">Implementacja <xref:System.Runtime.Serialization.ISerializable> obejmuje implementację `GetObjectData` metody i konstruktora specjalnego, który jest używany podczas deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-130">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="fe5b1-131">Poniższy przykładowy kod przedstawia sposób implementacji <xref:System.Runtime.Serialization.ISerializable> na `MyObject` klasie z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-131">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="fe5b1-132">Gdy **GetObjectData** jest wywoływana podczas serializacji, użytkownik jest odpowiedzialny za wypełnienie <xref:System.Runtime.Serialization.SerializationInfo> dostarczonego z wywołaniem metody.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-132">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="fe5b1-133">Dodaj serializowana jako pary nazw i wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-133">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="fe5b1-134">Tekst może służyć jako nazwę.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-134">Any text can be used as the name.</span></span> <span data-ttu-id="fe5b1-135">Możesz zdecydować, które zmienne składowe są dodawane do <xref:System.Runtime.Serialization.SerializationInfo>, pod warunkiem, że seializowane jest wystarczająco dużo danych, by można było przywrócić obiekt podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-135">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="fe5b1-136">Klasy pochodne powinny wywoływać metodę **GetObjectData** w obiekcie podstawowym, jeśli ta ostatnia implementuje <xref:System.Runtime.Serialization.ISerializable> .</span><span class="sxs-lookup"><span data-stu-id="fe5b1-136">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="fe5b1-137">Należy zauważyć, że serializacji może pozwalać na inny kod, aby wyświetlić lub zmodyfikować dane wystąpienia obiektu, który jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-137">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="fe5b1-138">W związku z tym kod, który wykonuje serializacji, wymaga [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określoną flagą.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-138">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="fe5b1-139">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-139">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="fe5b1-140">Metoda **GetObjectData** musi być jawnie chroniona przez wymaganie [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określoną flagą lub przez zajęcie innych uprawnień, które w sposób chroniący dane prywatne.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-140">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="fe5b1-141">Jeśli pole prywatne przechowuje poufne informacje, należy uzyskać odpowiednie uprawnienia w witrynie **GetObjectData** w celu ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-141">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="fe5b1-142">Należy pamiętać, że kod, który został przyznany [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z określoną flagą **SerializationFormatter** , może wyświetlać i modyfikować dane przechowywane w polach prywatnych.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-142">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="fe5b1-143">Złośliwy obiekt wywołujący, który udzielił tej [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) , może wyświetlać dane, takie jak ukryte Lokalizacje katalogów lub przyznane uprawnienia, a następnie używać danych w celu wykorzystania luki w zabezpieczeniach na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-143">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="fe5b1-144">Aby uzyskać pełną listę flag uprawnień zabezpieczeń, które można określić, zobacz [Wyliczenie SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="fe5b1-144">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="fe5b1-145"><xref:System.Runtime.Serialization.ISerializable>Należy zastanowić się, że kiedy jest dodawany do klasy, należy zaimplementować zarówno **GetObjectData** , jak i specjalny Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-145">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="fe5b1-146">Kompilator wyświetli ostrzeżenie, jeśli brakuje **GetObjectData** .</span><span class="sxs-lookup"><span data-stu-id="fe5b1-146">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="fe5b1-147">Jednak ponieważ nie można wymusić implementacji konstruktora, nie są wyświetlane żadne ostrzeżenia, jeśli Konstruktor jest nieobecny, a wyjątek jest zgłaszany podczas próby deserializacji klasy bez konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-147">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="fe5b1-148">Bieżący projekt został favored powyżej <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodę w celu obejściu potencjalne problemy dotyczące zabezpieczeń i przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-148">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="fe5b1-149">Na przykład `SetObjectData` Metoda musi być publiczna, jeśli jest zdefiniowana jako część interfejsu; w ten sposób użytkownicy muszą napisać kod w celu obrony przed przypisaniem metody **SetObjectData** wiele razy.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-149">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="fe5b1-150">W przeciwnym razie złośliwa aplikacja wywołująca metodę **SetObjectData** na obiekcie w procesie wykonywania operacji może spowodować potencjalne problemy.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-150">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="fe5b1-151">Podczas deserializacji <xref:System.Runtime.Serialization.SerializationInfo> została przekazana do klasy za pomocą konstruktora przewidzianej do tego celu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-151">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="fe5b1-152">Wszelkie ograniczenia widoczności umieszczone na Konstruktorze są ignorowane, gdy obiekt jest deserializowany; można oznaczyć klasę jako publiczną, chronioną, wewnętrzną lub prywatną.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-152">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="fe5b1-153">Jednak jest najlepszym rozwiązaniem, aby chronione, chyba że klasa jest zapieczętowany, w takim przypadku konstruktora powinien być oznaczony prywatnych konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-153">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="fe5b1-154">Konstruktor również należy wykonać dokładne sprawdzenie poprawności danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-154">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="fe5b1-155">Aby uniknąć nieprawidłowego użycia przez złośliwego kodu, konstruktora powinien wymuszać taką samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienie klasy za pomocą dowolnego innego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-155">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="fe5b1-156">Jeśli nie przestrzegasz tego zalecenia, złośliwy kod może preserializować obiekt, uzyskać kontrolę z [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określoną flagą i deserializować obiekt na komputerze klienckim, pomijając wszelkie zabezpieczenia, które zostałyby zastosowane podczas konstruowania wystąpienia standardowego przy użyciu konstruktora publicznego.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-156">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="fe5b1-157">Aby przywrócić stan obiektu, po prostu Pobierz wartości zmiennych z <xref:System.Runtime.Serialization.SerializationInfo> używania nazw używanych podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-157">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="fe5b1-158">Jeśli klasa bazowa implementuje <xref:System.Runtime.Serialization.ISerializable> , Konstruktor podstawowy powinien zostać wywołany, aby umożliwić obiektowi bazowemu przywrócenie zmiennych.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-158">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="fe5b1-159">Podczas wyprowadzania nowej klasy z klasy, która implementuje <xref:System.Runtime.Serialization.ISerializable> , Klasa pochodna musi implementować zarówno konstruktora, jak i metodę **GetObjectData** , jeśli ma zmienne, które muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-159">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="fe5b1-160">Poniższy przykład kodu pokazuje, jak to zrobić, przy użyciu `MyObject` klasy pokazanej wcześniej.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-160">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="fe5b1-161">Nie zapomnij wywołać klasy bazowej w konstruktorze deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-161">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="fe5b1-162">Jeśli to nie zrobisz, Konstruktor w klasie bazowej nigdy nie zostanie wywołany, a obiekt nie jest w pełni skonstruowany po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-162">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="fe5b1-163">Obiekty są odtworzone wewnątrz i wywołania metody podczas deserializacji może mieć niepożądane skutki uboczne, ponieważ metody o nazwie może odnosić się do odwołuje się do obiektu, które nie została przeprowadzona przez razem, gdy zostanie nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-163">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="fe5b1-164">Jeśli deserializowana Klasa implementuje <xref:System.Runtime.Serialization.IDeserializationCallback> <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> metodę, metoda jest wywoływana automatycznie, gdy zostanie odszeregowany cały Graf obiektu.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-164">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="fe5b1-165">Na tym etapie wszystkie obiekty podrzędne, do których odwołuje się zostały w pełni przywrócone.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-165">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="fe5b1-166">Tablica skrótów jest typowym przykładem klasy, która jest trudna do deserializacji bez użycia odbiornika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-166">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="fe5b1-167">Łatwo można pobrać par kluczy i wartości podczas deserializacji, ale dodanie tych obiektów do tabeli mieszania może spowodować problemy, ponieważ nie ma żadnej gwarancji tej klasy, które opracowane na podstawie tabeli mieszania deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-167">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="fe5b1-168">Wywołanie metody w tabeli mieszania na tym etapie z tego powodu nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="fe5b1-168">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5b1-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe5b1-169">See also</span></span>

- [<span data-ttu-id="fe5b1-170">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="fe5b1-170">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="fe5b1-171">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="fe5b1-171">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="fe5b1-172">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="fe5b1-172">Security and Serialization</span></span>](../../framework/misc/security-and-serialization.md)
