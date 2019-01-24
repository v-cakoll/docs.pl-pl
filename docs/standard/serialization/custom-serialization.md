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
ms.openlocfilehash: 83538dc971419ad7918c16c5ccbd2003d16e2c6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627999"
---
# <a name="custom-serialization"></a>Niestandardowej serializacji
Niestandardowej serializacji to proces sterowania serializacji i deserializacji obiektu określonego typu. Kontrolując serializacji jest możliwe w celu zapewnienia zgodności serializacji, które jest możliwość serializacji i deserializacji pomiędzy wersjami typu bez przerywania podstawowych funkcji typu. Na przykład w pierwszej wersji typu, może istnieć tylko dwa pola. W następnej wersji typu są dodawane kilka więcej pól. Jeszcze drugi wersji aplikacji, musi mieć możliwość serializacji i deserializacji oba typy. W następujących sekcjach opisano kontrola serializacji.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
>  W wersjach wcześniejszych niż .NET Framework 4.0 serializacji danych niestandardowych użytkownika w częściowo zaufanym zestawem było wykonywane na metodę GetObjectData. Począwszy od wersji 4.0, metoda jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, co uniemożliwia wykonanie w częściowo zaufanych zestawów. Aby obejść ten problem, należy zaimplementować <xref:System.Runtime.Serialization.ISafeSerializationData> interfejsu.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Uruchamianie niestandardowych metod w trakcie i po serializacji  
 Najlepsze praktyki i najłatwiejszy sposób (wprowadzona w wersji 2.0 programu .NET Framework) stosuje się następujące atrybuty do metody, które są używane do poprawnych danych podczas i po serializacji:  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Te atrybuty zezwalać na typ do korzystania z jednej z lub wszystkie cztery fazy procesy serializacji i deserializacji. Atrybuty określają metody, które powinny być używane w fazie każdego typu. Metody nie uzyskać dostępu do strumienia serializacji, ale umożliwiają zamiast tego można zmieniać przed i po serializacji, lub przed i po deserializacji obiektu. Atrybuty można zastosować na wszystkich poziomach hierarchii dziedziczenia typu, a każda metoda jest wywoływana w hierarchii od podstawy do najbardziej pochodnej. Ten mechanizm pozwala uniknąć złożoności i wszelkie problemy wynikowe stosowania <xref:System.Runtime.Serialization.ISerializable> interfejsu, zapewniając odpowiedzialność za serializacji i deserializacji w celu wykonania najbardziej pochodnej. Ponadto ten mechanizm pozwala elementy formatujące do ignorowania populacji pola i pobieranie ze strumienia serializacji. Szczegóły i kontrolowanie serializacji i deserializacji przykłady kliknij dowolne z poprzednich łącza.  
  
 Ponadto, dodając nowe pole do istniejącego typu serializacji, zastosuj <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybutu do pola. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje braku pola podczas przetwarzania strumienia, w którym brakuje nowe pole.  
  
## <a name="implementing-the-iserializable-interface"></a>Implementującej interfejs ISerializable  
 Inny sposób kontroluje serializacji uzyskuje się dzięki wdrożeniu <xref:System.Runtime.Serialization.ISerializable> interfejs do obiektu. Należy jednak pamiętać, że metoda w poprzedniej sekcji zastępuje tę metodę w celu sterowania serializacji.  
  
 Ponadto nie należy używać serializacji domyślny na klasę, która jest oznaczona za pomocą [Serializable](xref:System.SerializableAttribute) atrybutu i deklaratywne lub nadrzędnych zabezpieczeń na poziomie klasy lub w jego konstruktorów. Zamiast tego należy zawsze wdrożenia tych klas <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
 Implementowanie <xref:System.Runtime.Serialization.ISerializable> polega na implementowanie `GetObjectData` metody i specjalnych konstruktora, który jest używany, gdy deserializowany jest obiekt. Następujący przykładowy kod przedstawia sposób implementowania <xref:System.Runtime.Serialization.ISerializable> na `MyObject` klasy z poprzedniej sekcji.  
  
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
  
 Gdy **metodę GetObjectData** jest wywoływana podczas serializacji, jesteś odpowiedzialny za wypełnianie <xref:System.Runtime.Serialization.SerializationInfo> dostarczane z wywołania metody. Dodaj serializowana jako pary nazw i wartości zmiennych. Tekst może służyć jako nazwę. Możesz zdecydować, które zmienne składowe są dodawane do <xref:System.Runtime.Serialization.SerializationInfo>, pod warunkiem, że seializowane jest wystarczająco dużo danych, by można było przywrócić obiekt podczas deserializacji. Klasach pochodnych należy wywołać **metodę GetObjectData** metody dla obiektu podstawowego Jeśli ostatnie implementuje <xref:System.Runtime.Serialization.ISerializable>.  
  
 Należy zauważyć, że serializacji może pozwalać na inny kod, aby wyświetlić lub zmodyfikować dane wystąpienia obiektu, który jest niedostępny. W związku z tym, wymaga kodu, który będzie wykonywać serializacji [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> określono flagę. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym. **Metodę GetObjectData** metody musi być jawnie chroniony, po wymagających [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagi określono lub przez wymagających inne uprawnienia, które w szczególności pomocy Chroń dane prywatne.  
  
 Jeśli pole private są przechowywane poufne informacje, należy zażądać odpowiednie uprawnienia na **metodę GetObjectData** do ochrony danych. Należy pamiętać, ten kod, któremu udzielono [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z **SerializationFormatter** określono flagę można wyświetlać i modyfikować dane przechowywane w pól prywatnych. Osoby wywołującej złośliwego przyznania [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) można wyświetlić dane, takie jak lokalizacjach ukryte katalogu lub uprawnienia udzielane i wykorzystać luki w zabezpieczeniach na komputerze przy użyciu danych. Aby uzyskać pełną listę flag uprawnień zabezpieczeń, można określić, zobacz [wyliczenia SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Ważne jest, aby podkreślają, że po <xref:System.Runtime.Serialization.ISerializable> jest dodawany do klasy należy zaimplementować obu **metodę GetObjectData** i specjalnych konstruktora. Kompilator wyświetla ostrzeżenie, jeśli **metodę GetObjectData** są spełnione. Jednak ponieważ nie jest możliwe do wymuszenia wykonania konstruktora, ostrzeżenie nie jest zapewniona, jeśli ma konstruktora i zgłaszany jest wyjątek podczas próby deserializacji klasę bez konstruktora.  
  
 Bieżący projekt został favored powyżej <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodę w celu obejściu potencjalne problemy dotyczące zabezpieczeń i przechowywania wersji. Na przykład `SetObjectData` metody muszą być publiczne, jeśli jest on zdefiniowany jako część interfejs; w związku z tym użytkownicy muszą pisanie kodu do obrony przed o **SetObjectData** metodę wywoływać wielokrotnie. W przeciwnym razie złośliwy aplikacji wywołujących **SetObjectData** metody na obiekt w trakcie wykonywania operacji może spowodować potencjalne problemy.  
  
 Podczas deserializacji <xref:System.Runtime.Serialization.SerializationInfo> została przekazana do klasy za pomocą konstruktora przewidzianej do tego celu. Wszelkich ograniczeń widoczność umieścić w Konstruktorze są ignorowane, gdy deserializowany; dlatego można oznaczyć klasę jako publicznych, chronionych, wewnętrzny lub prywatny. Jednak jest najlepszym rozwiązaniem, aby chronione, chyba że klasa jest zapieczętowany, w takim przypadku konstruktora powinien być oznaczony prywatnych konstruktora. Konstruktor również należy wykonać dokładne sprawdzenie poprawności danych wejściowych. Aby uniknąć nieprawidłowego użycia przez złośliwego kodu, konstruktora powinien wymuszać taką samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienie klasy za pomocą dowolnego innego konstruktora. Jeśli nie wykonuj tej rekomendacji, złośliwy kod może preserialize obiektu, uzyskać kontrolę przy użyciu [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> Flaga określony i deserializacji obiektu na komputerze klienckim, z pominięciem dowolne zabezpieczenia, która będzie stosowana podczas konstruowania wystąpienia standard przy użyciu publicznego konstruktora.  
  
 Aby przywrócić stan obiektu, wystarczy pobrać wartości zmiennych z <xref:System.Runtime.Serialization.SerializationInfo> przy użyciu nazwy używane podczas serializacji. Jeśli klasa bazowa implementuje <xref:System.Runtime.Serialization.ISerializable>, podstawowa konstruktora powinna być wywoływana umożliwiające obiektu podstawowego do przywrócenia jego zmiennych.  
  
 Po utworzeniu klasy pochodnej nową klasę z jednego, który implementuje <xref:System.Runtime.Serialization.ISerializable>, klasy pochodnej musi implementować zarówno konstruktora, jak również **metodę GetObjectData** metoda ma zmienne, które muszą być serializowane. Poniższy przykład kodu pokazuje, jak to zrobić za pomocą `MyObject` klasy wyświetlane wcześniej.  
  
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
  
 Nie zapomnij wywołać klasy bazowej w Konstruktorze deserializacji. Jeśli to nie jest wykonywane, nigdy nie wywołania konstruktora dla klasy bazowej, a obiekt nie jest w pełni skonstruować po deserializacji.  
  
 Obiekty są odtworzone wewnątrz i wywołania metody podczas deserializacji może mieć niepożądane skutki uboczne, ponieważ metody o nazwie może odnosić się do odwołuje się do obiektu, które nie została przeprowadzona przez razem, gdy zostanie nawiązane połączenie. Jeśli deserializowane klasa implementuje <xref:System.Runtime.Serialization.IDeserializationCallback>, <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> metoda jest wywoływana automatycznie, gdy wykonać deserializacji wykresu cały obiekt. Na tym etapie wszystkie obiekty podrzędne, do których odwołuje się zostały w pełni przywrócone. Tabela skrótu jest typowym przykładem klasę, która jest trudne do deserializacji bez użycia odbiornik zdarzenia. Łatwo można pobrać par kluczy i wartości podczas deserializacji, ale dodanie tych obiektów do tabeli mieszania może spowodować problemy, ponieważ nie ma żadnej gwarancji tej klasy, które opracowane na podstawie tabeli mieszania deserializacji. Wywołanie metody w tabeli mieszania na tym etapie z tego powodu nie jest zalecane.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
