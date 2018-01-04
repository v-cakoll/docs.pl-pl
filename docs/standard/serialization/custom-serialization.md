---
title: Niestandardowej serializacji
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5718f19318121c2025b9d92a5947574289c1f4d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="custom-serialization"></a>Niestandardowej serializacji
Niestandardowej serializacji to proces sterowania serializacji i deserializacji obiektu określonego typu. Kontrolowanie serializacji, jest możliwe w celu zapewnienia zgodności serializacji, który jest możliwość serializowania i deserializowania między wersjami typu bez przerywania podstawowych funkcji typu. Na przykład w pierwszej wersji typu, może istnieć tylko dwa pola. W następnej wersji typu są dodawane kilka więcej pól. Jeszcze druga wersja aplikacji musi mieć możliwość serializowania i deserializowania obu typów. W następujących sekcjach opisano kontrola serializacji.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  W wersjach starszych niż program .NET Framework 4.0 serializacji danych użytkownika niestandardowego w częściowo zaufanym zestawie zostało realizowane przy użyciu GetObjectData. Począwszy od wersji 4.0, metoda jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, co uniemożliwia wykonanie w częściowo zaufanych zestawów. Aby obejść ten warunek, zaimplementuj <xref:System.Runtime.Serialization.ISafeSerializationData> interfejsu.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Uruchamianie niestandardowych metod podczas i po serializacji  
 Najlepsze praktyki i Najprostszym sposobem (wprowadzonych w wersji 2.0 programu .NET Framework) stosuje się następujące atrybuty do metod, które są używane do poprawnych danych podczas i po serializacji:  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Te atrybuty zezwalać na typ do korzystania z jednej z lub wszystkie cztery fazy procesy serializacji i deserializacji. Atrybuty określają metody, które powinny być używane w fazie każdego typu. Metody nie uzyskać dostępu do strumienia serializacji, ale umożliwiają zamiast tego można zmieniać przed i po serializacji, lub przed i po deserializacji obiektu. Atrybuty można zastosować na wszystkich poziomach hierarchii dziedziczenia typu, a każda metoda jest wywoływana w hierarchii od podstawy do najbardziej pochodnej. Ten mechanizm pozwala uniknąć złożoność i problemy wynikowy wykonawczych <xref:System.Runtime.Serialization.ISerializable> interfejsu, zapewniając odpowiedzialność za serializacji i deserializacji w celu wykonania najdalszych pochodnych. Ponadto ten mechanizm pozwala elementy formatujące do ignorowania populacji pola i pobieranie ze strumienia serializacji. Szczegółowe informacje i przykłady kontrolowanie serializacji i deserializacji kliknij dowolne z poprzednich łączy.  
  
 Ponadto, dodając nowe pole do istniejącego typu serializacji, zastosuj <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do pola. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje braku pola podczas przetwarzania strumienia, w którym brakuje nowe pole.  
  
## <a name="implementing-the-iserializable-interface"></a>Implementacja interfejsu ISerializable  
 Innym sposobem sterowania serializacją uzyskuje się poprzez wdrożenie <xref:System.Runtime.Serialization.ISerializable> interfejsu dla obiektu. Należy jednak pamiętać, że metoda w poprzedniej sekcji zastępuje tę metodę w celu sterowania serializacji.  
  
 Ponadto nie należy używać domyślnej serializacji dla klasy, która jest oznaczony atrybutem [Serializable](xref:System.SerializableAttribute) atrybutu i deklaratywne lub imperatywnych zabezpieczeń na poziomie klasy lub na jego konstruktorów. Zamiast tego należy zawsze należy zaimplementować te klasy <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
 Implementowanie <xref:System.Runtime.Serialization.ISerializable> obejmuje implementacja `GetObjectData` — metoda i specjalnych konstruktora, który jest używany podczas deserializowany jest obiekt. Następujący przykładowy kod przedstawia sposób wykonania <xref:System.Runtime.Serialization.ISerializable> na `MyObject` klasy z poprzedniej sekcji.  
  
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
  
 Gdy **GetObjectData** jest wywoływana podczas serializacji, jest odpowiedzialny za wypełnianie <xref:System.Runtime.Serialization.SerializationInfo> podany przy wywołaniu metody. Dodaj serializowana jako pary nazw i wartości zmiennych. Tekst może służyć jako nazwę. Możesz zdecydować, które zmienne składowe są dodawane do <xref:System.Runtime.Serialization.SerializationInfo>, pod warunkiem, że seializowane jest wystarczająco dużo danych, by można było przywrócić obiekt podczas deserializacji. Klasy pochodne powinny wywoływać **GetObjectData** metody dla obiektu podstawowego Jeśli ostatnie implementuje <xref:System.Runtime.Serialization.ISerializable>.  
  
 Należy zauważyć, że serializacji może pozwalać na inny kod, aby wyświetlić lub zmodyfikować dane wystąpienia obiektu, który jest niedostępny. W związku z tym wymaga kod wykonujący serializacji [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określona flaga. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym. **GetObjectData** metody muszą być jawnie chronione, przez wymagających [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagi określone lub wymagających przez inne uprawnienia, które pomagają w szczególności chronić dane prywatne.  
  
 Jeśli pole prywatne są przechowywane poufne informacje, należy zażądać odpowiednie uprawnienia na **GetObjectData** do ochrony danych. Należy pamiętać, ten kod, który został udzielony [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z **SerializationFormatter** określona flaga można wyświetlać i modyfikować dane przechowywane w pól prywatnych. Obiekt wywołujący złośliwego przyznania [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) można wyświetlić dane, takie jak lokalizacje katalogiem ukrytym lub przyznanych uprawnień i wykorzystać luki w zabezpieczeniach na komputerze przy użyciu danych. Aby uzyskać pełną listę flag uprawnień zabezpieczeń, można określić, zobacz [wyliczenie SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Jest podkreślić, że w przypadku <xref:System.Runtime.Serialization.ISerializable> jest dodawana do klasy należy zaimplementować zarówno **GetObjectData** i specjalnych konstruktora. Kompilator wyświetli ostrzeżenie, jeśli **GetObjectData** brakuje. Jednak ponieważ nie jest możliwe wymusić implementacji konstruktora, bez ostrzeżenia jest podany, jeśli nie ma konstruktora i jest zgłaszany wyjątek podczas próby deserializacji klasy bez konstruktora.  
  
 Bieżący projekt został favored powyżej <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodę w celu obejściu potencjalne problemy dotyczące zabezpieczeń i przechowywania wersji. Na przykład `SetObjectData` metody muszą być publiczne, jeśli jest on zdefiniowany jako część interfejsu; w związku z tym użytkownicy napisać kod do ochrony przed o **SetObjectData** Metoda wywołana wiele razy. W przeciwnym razie złośliwego aplikacji wywołujących **SetObjectData** metoda obiektu w trakcie wykonywania operacji może spowodować potencjalne problemy.  
  
 Podczas deserializacji <xref:System.Runtime.Serialization.SerializationInfo> została przekazana do klasy za pomocą konstruktora przewidzianej do tego celu. Wszystkie ograniczenia widoczności konstruktora są ignorowane w przypadku deserializowany jest obiekt; Dlatego klasy można oznaczyć jako publiczny, chroniony, wewnętrzny ani prywatny. Jednak jest najlepszym rozwiązaniem, aby chronione, chyba że klasa jest zapieczętowany, w takim przypadku konstruktora powinien być oznaczony prywatnych konstruktora. Konstruktor również należy wykonać dokładne sprawdzenie poprawności danych wejściowych. Aby uniknąć nieprawidłowego użycia przez złośliwego kodu, konstruktora powinien wymuszać taką samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienie klasy za pomocą dowolnego innego konstruktora. Jeśli to zalecenie nie jest zgodna, złośliwy kod może preserialize obiektu, uzyskać formantu o [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagi określone i przeprowadzić deserializacji obiektu na komputerze klienckim, pomijając jedną zabezpieczenia, która będzie stosowana podczas konstruowania standardowe wystąpienia przy użyciu konstruktora publicznego.  
  
 Aby przywrócić stan obiektu, wystarczy pobrać wartości zmiennych z <xref:System.Runtime.Serialization.SerializationInfo> przy użyciu nazw używanych podczas serializacji. Jeśli implementuje klasy podstawowej <xref:System.Runtime.Serialization.ISerializable>, należy wywołać konstruktora podstawowego umożliwia obiektu podstawowego przywrócić jego zmiennych.  
  
 Jeśli pochodzi nową klasę z jednego, który implementuje <xref:System.Runtime.Serialization.ISerializable>, klasa pochodna musi implementować zarówno konstruktora, jak również **GetObjectData** metodę, jeśli ma ona zmienne, które muszą być serializowane. Poniższy przykład kodu pokazuje, jak to zrobić przy użyciu `MyObject` klasy przedstawione wcześniej.  
  
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
  
 Nie zapomnij Wywołaj klasę bazową w Konstruktorze deserializacji. Jeśli to nie jest nigdy nie wywołania konstruktora dla klasy podstawowej, a obiekt nie jest dokończony po deserializacji.  
  
 Obiekty są odtworzone wewnątrz i wywołania metody podczas deserializacji może mieć niepożądane skutki uboczne, ponieważ metody o nazwie może odnosić się do odwołuje się do obiektu, które nie została przeprowadzona przez razem, gdy zostanie nawiązane połączenie. Jeśli deserializowane klasa implementuje <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> metoda jest wywoływana automatycznie, gdy przeprowadzić deserializacji grafu całego obiektu. Na tym etapie wszystkie obiekty podrzędne, do których odwołuje się zostały w pełni przywrócone. Tabela skrótów jest typowym przykładem klasę, która jest trudne do deserializacji bez użycia odbiornik zdarzeń. Łatwo można pobrać par kluczy i wartości podczas deserializacji, ale dodanie tych obiektów do tabeli mieszania może spowodować problemy, ponieważ nie ma żadnej gwarancji tej klasy, które opracowane na podstawie tabeli mieszania deserializacji. Wywołanie metody w tabeli mieszania na tym etapie z tego powodu nie jest zalecane.  
  
## <a name="see-also"></a>Zobacz także  
 [Serializacja binarna](binary-serialization.md)  
 [Serializacja XML i SOAP](xml-and-soap-serialization.md)  
 [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
