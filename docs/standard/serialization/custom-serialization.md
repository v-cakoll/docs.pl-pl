---
title: Niestandardowej serializacji
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
ms.openlocfilehash: 79cb7a2a0706cb06cbd444f4a2e1ae87cb701101
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592109"
---
# <a name="custom-serialization"></a><span data-ttu-id="906da-102">Niestandardowej serializacji</span><span class="sxs-lookup"><span data-stu-id="906da-102">Custom serialization</span></span>
<span data-ttu-id="906da-103">Niestandardowej serializacji to proces sterowania serializacji i deserializacji obiektu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="906da-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="906da-104">Kontrolowanie serializacji, jest możliwe w celu zapewnienia zgodności serializacji, który jest możliwość serializowania i deserializowania między wersjami typu bez przerywania podstawowych funkcji typu.</span><span class="sxs-lookup"><span data-stu-id="906da-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="906da-105">Na przykład w pierwszej wersji typu, może istnieć tylko dwa pola.</span><span class="sxs-lookup"><span data-stu-id="906da-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="906da-106">W następnej wersji typu są dodawane kilka więcej pól.</span><span class="sxs-lookup"><span data-stu-id="906da-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="906da-107">Jeszcze druga wersja aplikacji musi mieć możliwość serializowania i deserializowania obu typów.</span><span class="sxs-lookup"><span data-stu-id="906da-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="906da-108">W następujących sekcjach opisano kontrola serializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  <span data-ttu-id="906da-109">W wersjach starszych niż program .NET Framework 4.0 serializacji danych użytkownika niestandardowego w częściowo zaufanym zestawie zostało realizowane przy użyciu GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="906da-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="906da-110">Począwszy od wersji 4.0, metoda jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, co uniemożliwia wykonanie w częściowo zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="906da-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="906da-111">Aby obejść ten warunek, zaimplementuj <xref:System.Runtime.Serialization.ISafeSerializationData> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="906da-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="906da-112">Uruchamianie niestandardowych metod podczas i po serializacji</span><span class="sxs-lookup"><span data-stu-id="906da-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="906da-113">Najlepsze praktyki i Najprostszym sposobem (wprowadzonych w wersji 2.0 programu .NET Framework) stosuje się następujące atrybuty do metod, które są używane do poprawnych danych podczas i po serializacji:</span><span class="sxs-lookup"><span data-stu-id="906da-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="906da-114">Te atrybuty zezwalać na typ do korzystania z jednej z lub wszystkie cztery fazy procesy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="906da-115">Atrybuty określają metody, które powinny być używane w fazie każdego typu.</span><span class="sxs-lookup"><span data-stu-id="906da-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="906da-116">Metody nie uzyskać dostępu do strumienia serializacji, ale umożliwiają zamiast tego można zmieniać przed i po serializacji, lub przed i po deserializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="906da-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="906da-117">Atrybuty można zastosować na wszystkich poziomach hierarchii dziedziczenia typu, a każda metoda jest wywoływana w hierarchii od podstawy do najbardziej pochodnej.</span><span class="sxs-lookup"><span data-stu-id="906da-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="906da-118">Ten mechanizm pozwala uniknąć złożoność i problemy wynikowy wykonawczych <xref:System.Runtime.Serialization.ISerializable> interfejsu, zapewniając odpowiedzialność za serializacji i deserializacji w celu wykonania najdalszych pochodnych.</span><span class="sxs-lookup"><span data-stu-id="906da-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="906da-119">Ponadto ten mechanizm pozwala elementy formatujące do ignorowania populacji pola i pobieranie ze strumienia serializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="906da-120">Szczegółowe informacje i przykłady kontrolowanie serializacji i deserializacji kliknij dowolne z poprzednich łączy.</span><span class="sxs-lookup"><span data-stu-id="906da-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="906da-121">Ponadto, dodając nowe pole do istniejącego typu serializacji, zastosuj <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do pola.</span><span class="sxs-lookup"><span data-stu-id="906da-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="906da-122"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje braku pola podczas przetwarzania strumienia, w którym brakuje nowe pole.</span><span class="sxs-lookup"><span data-stu-id="906da-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="906da-123">Implementacja interfejsu ISerializable</span><span class="sxs-lookup"><span data-stu-id="906da-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="906da-124">Innym sposobem sterowania serializacją uzyskuje się poprzez wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="906da-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="906da-125">Należy jednak pamiętać, że metoda w poprzedniej sekcji zastępuje tę metodę w celu sterowania serializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="906da-126">Ponadto nie należy używać domyślnej serializacji dla klasy, która jest oznaczony atrybutem [Serializable](xref:System.SerializableAttribute) atrybutu i deklaratywne lub imperatywnych zabezpieczeń na poziomie klasy lub na jego konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="906da-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="906da-127">Zamiast tego należy zawsze należy zaimplementować te klasy <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="906da-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="906da-128">Implementowanie <xref:System.Runtime.Serialization.ISerializable> obejmuje implementacja `GetObjectData` — metoda i specjalnych konstruktora, który jest używany podczas deserializowany jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="906da-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="906da-129">Następujący przykładowy kod przedstawia sposób wykonania <xref:System.Runtime.Serialization.ISerializable> na `MyObject` klasy z poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="906da-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
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
[SecurityPermissionAttribute(SecurityAction.Demand,   
SerializationFormatter =true)]  
  
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
  
    Protected Sub New(ByVal info As SerializationInfo, _  
    ByVal context As StreamingContext)   
        n1 = info.GetInt32("i")  
        n2 = info.GetInt32("j")  
        str = info.GetString("k")  
    End Sub 'New  
  
    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _  
    Public Overridable Sub GetObjectData(ByVal info As _  
    SerializationInfo, ByVal context As StreamingContext)   
        info.AddValue("i", n1)  
        info.AddValue("j", n2)  
        info.AddValue("k", str)  
    End Sub   
End Class  
```  
  
 <span data-ttu-id="906da-130">Gdy **GetObjectData** jest wywoływana podczas serializacji, jest odpowiedzialny za wypełnianie <xref:System.Runtime.Serialization.SerializationInfo> podany przy wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="906da-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="906da-131">Dodaj serializowana jako pary nazw i wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="906da-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="906da-132">Tekst może służyć jako nazwę.</span><span class="sxs-lookup"><span data-stu-id="906da-132">Any text can be used as the name.</span></span> <span data-ttu-id="906da-133">Możesz zdecydować, które zmienne składowe są dodawane do <xref:System.Runtime.Serialization.SerializationInfo>, pod warunkiem, że seializowane jest wystarczająco dużo danych, by można było przywrócić obiekt podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="906da-134">Klasy pochodne powinny wywoływać **GetObjectData** metody dla obiektu podstawowego Jeśli ostatnie implementuje <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="906da-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="906da-135">Należy zauważyć, że serializacji może pozwalać na inny kod, aby wyświetlić lub zmodyfikować dane wystąpienia obiektu, który jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="906da-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="906da-136">W związku z tym wymaga kod wykonujący serializacji [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określona flaga.</span><span class="sxs-lookup"><span data-stu-id="906da-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="906da-137">W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="906da-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="906da-138">**GetObjectData** metody muszą być jawnie chronione, przez wymagających [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagi określone lub wymagających przez inne uprawnienia, które pomagają w szczególności chronić dane prywatne.</span><span class="sxs-lookup"><span data-stu-id="906da-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="906da-139">Jeśli pole prywatne są przechowywane poufne informacje, należy zażądać odpowiednie uprawnienia na **GetObjectData** do ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="906da-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="906da-140">Należy pamiętać, ten kod, który został udzielony [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z **SerializationFormatter** określona flaga można wyświetlać i modyfikować dane przechowywane w pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="906da-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="906da-141">Obiekt wywołujący złośliwego przyznania [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) można wyświetlić dane, takie jak lokalizacje katalogiem ukrytym lub przyznanych uprawnień i wykorzystać luki w zabezpieczeniach na komputerze przy użyciu danych.</span><span class="sxs-lookup"><span data-stu-id="906da-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="906da-142">Aby uzyskać pełną listę flag uprawnień zabezpieczeń, można określić, zobacz [wyliczenie SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="906da-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="906da-143">Jest podkreślić, że w przypadku <xref:System.Runtime.Serialization.ISerializable> jest dodawana do klasy należy zaimplementować zarówno **GetObjectData** i specjalnych konstruktora.</span><span class="sxs-lookup"><span data-stu-id="906da-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="906da-144">Kompilator wyświetli ostrzeżenie, jeśli **GetObjectData** brakuje.</span><span class="sxs-lookup"><span data-stu-id="906da-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="906da-145">Jednak ponieważ nie jest możliwe wymusić implementacji konstruktora, bez ostrzeżenia jest podany, jeśli nie ma konstruktora i jest zgłaszany wyjątek podczas próby deserializacji klasy bez konstruktora.</span><span class="sxs-lookup"><span data-stu-id="906da-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="906da-146">Bieżący projekt został favored powyżej <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodę w celu obejściu potencjalne problemy dotyczące zabezpieczeń i przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="906da-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="906da-147">Na przykład `SetObjectData` metody muszą być publiczne, jeśli jest on zdefiniowany jako część interfejsu; w związku z tym użytkownicy napisać kod do ochrony przed o **SetObjectData** Metoda wywołana wiele razy.</span><span class="sxs-lookup"><span data-stu-id="906da-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="906da-148">W przeciwnym razie złośliwego aplikacji wywołujących **SetObjectData** metoda obiektu w trakcie wykonywania operacji może spowodować potencjalne problemy.</span><span class="sxs-lookup"><span data-stu-id="906da-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="906da-149">Podczas deserializacji <xref:System.Runtime.Serialization.SerializationInfo> została przekazana do klasy za pomocą konstruktora przewidzianej do tego celu.</span><span class="sxs-lookup"><span data-stu-id="906da-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="906da-150">Wszystkie ograniczenia widoczności konstruktora są ignorowane w przypadku deserializowany jest obiekt; Dlatego klasy można oznaczyć jako publiczny, chroniony, wewnętrzny ani prywatny.</span><span class="sxs-lookup"><span data-stu-id="906da-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="906da-151">Jednak jest najlepszym rozwiązaniem, aby chronione, chyba że klasa jest zapieczętowany, w takim przypadku konstruktora powinien być oznaczony prywatnych konstruktora.</span><span class="sxs-lookup"><span data-stu-id="906da-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="906da-152">Konstruktor również należy wykonać dokładne sprawdzenie poprawności danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="906da-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="906da-153">Aby uniknąć nieprawidłowego użycia przez złośliwego kodu, konstruktora powinien wymuszać taką samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienie klasy za pomocą dowolnego innego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="906da-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="906da-154">Jeśli to zalecenie nie jest zgodna, złośliwy kod może preserialize obiektu, uzyskać formantu o [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagi określone i przeprowadzić deserializacji obiektu na komputerze klienckim, pomijając jedną zabezpieczenia, która będzie stosowana podczas konstruowania standardowe wystąpienia przy użyciu konstruktora publicznego.</span><span class="sxs-lookup"><span data-stu-id="906da-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="906da-155">Aby przywrócić stan obiektu, wystarczy pobrać wartości zmiennych z <xref:System.Runtime.Serialization.SerializationInfo> przy użyciu nazw używanych podczas serializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="906da-156">Jeśli implementuje klasy podstawowej <xref:System.Runtime.Serialization.ISerializable>, należy wywołać konstruktora podstawowego umożliwia obiektu podstawowego przywrócić jego zmiennych.</span><span class="sxs-lookup"><span data-stu-id="906da-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="906da-157">Jeśli pochodzi nową klasę z jednego, który implementuje <xref:System.Runtime.Serialization.ISerializable>, klasa pochodna musi implementować zarówno konstruktora, jak również **GetObjectData** metodę, jeśli ma ona zmienne, które muszą być serializowane.</span><span class="sxs-lookup"><span data-stu-id="906da-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="906da-158">Poniższy przykład kodu pokazuje, jak to zrobić przy użyciu `MyObject` klasy przedstawione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="906da-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp  
[Serializable]  
public class ObjectTwo : MyObject  
{  
    public int num;  
  
    public ObjectTwo() : base()  
    {  
    }  
  
    protected ObjectTwo(SerializationInfo si,   
    StreamingContext context) : base(si,context)  
    {  
        num = si.GetInt32("num");  
    }  
[SecurityPermissionAttribute(SecurityAction.Demand,  
SerializationFormatter = true)]  
    public override void GetObjectData(SerializationInfo si,   
    StreamingContext context)  
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
  
    <SecurityPermissionAttribute(SecurityAction.Demand, _  
    SerializationFormatter := True)>  _  
    Public Overrides Sub GetObjectData(ByVal si As _  
    SerializationInfo, ByVal context As StreamingContext)   
        MyBase.GetObjectData(si, context)  
        si.AddValue("num", num)      
    End Sub   
End Class  
```  
  
 <span data-ttu-id="906da-159">Nie zapomnij Wywołaj klasę bazową w Konstruktorze deserializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="906da-160">Jeśli to nie jest nigdy nie wywołania konstruktora dla klasy podstawowej, a obiekt nie jest dokończony po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="906da-161">Obiekty są odtworzone wewnątrz i wywołania metody podczas deserializacji może mieć niepożądane skutki uboczne, ponieważ metody o nazwie może odnosić się do odwołuje się do obiektu, które nie została przeprowadzona przez razem, gdy zostanie nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="906da-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="906da-162">Jeśli deserializowane klasa implementuje <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> metoda jest wywoływana automatycznie, gdy przeprowadzić deserializacji grafu całego obiektu.</span><span class="sxs-lookup"><span data-stu-id="906da-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="906da-163">Na tym etapie wszystkie obiekty podrzędne, do których odwołuje się zostały w pełni przywrócone.</span><span class="sxs-lookup"><span data-stu-id="906da-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="906da-164">Tabela skrótów jest typowym przykładem klasę, która jest trudne do deserializacji bez użycia odbiornik zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="906da-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="906da-165">Łatwo można pobrać par kluczy i wartości podczas deserializacji, ale dodanie tych obiektów do tabeli mieszania może spowodować problemy, ponieważ nie ma żadnej gwarancji tej klasy, które opracowane na podstawie tabeli mieszania deserializacji.</span><span class="sxs-lookup"><span data-stu-id="906da-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="906da-166">Wywołanie metody w tabeli mieszania na tym etapie z tego powodu nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="906da-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906da-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="906da-167">See also</span></span>  
 [<span data-ttu-id="906da-168">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="906da-168">Binary Serialization</span></span>](binary-serialization.md)  
 [<span data-ttu-id="906da-169">Serializacja XML i SOAP</span><span class="sxs-lookup"><span data-stu-id="906da-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)  
 [<span data-ttu-id="906da-170">Zabezpieczenia i serializacja</span><span class="sxs-lookup"><span data-stu-id="906da-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
