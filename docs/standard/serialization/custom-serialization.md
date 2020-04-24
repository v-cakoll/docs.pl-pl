---
title: Serializacja niestandardowa
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
ms.openlocfilehash: 60fdc0317975d94433401e3214953b77d0970f60
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741057"
---
# <a name="custom-serialization"></a>Serializacja niestandardowa
Niestandardowej serializacji to proces sterowania serializacji i deserializacji obiektu określonego typu. Kontrolując serializacji, można zapewnić zgodność serializacji, która jest możliwością serializacji i deserializacji między wersjami typu bez przerywania podstawowej funkcjonalności typu. Na przykład w pierwszej wersji typu mogą istnieć tylko dwa pola. W następnej wersji typu są dodawane kilka więcej pól. Jeszcze druga wersja aplikacji musi mieć możliwość serializacji i deserializacji obu typów. W następujących sekcjach opisano kontrola serializacji.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> W wersjach wcześniejszych niż .NET Framework 4,0 Serializacja niestandardowych danych użytkownika w częściowo zaufanym zestawie została zrealizowana przy użyciu GetObjectData. Począwszy od wersji 4.0, metoda jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, co uniemożliwia wykonanie w częściowo zaufanych zestawów. Aby obejść ten warunek, zaimplementuj <xref:System.Runtime.Serialization.ISafeSerializationData> interfejs.  
  
## <a name="running-custom-methods-during-and-after-serialization"></a>Uruchamianie metod niestandardowych w trakcie serializacji i po nim  
 Najlepszym rozwiązaniem i najprostszym sposobem (wprowadzonym w wersji 2,0 .NET Framework) jest stosowanie następujących atrybutów do metod, które są używane do poprawiania danych podczas serializacji i po nim:  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 Te atrybuty zezwalać na typ do korzystania z jednej z lub wszystkie cztery fazy procesy serializacji i deserializacji. Atrybuty określają metody, które powinny być używane w fazie każdego typu. Metody nie uzyskać dostępu do strumienia serializacji, ale umożliwiają zamiast tego można zmieniać przed i po serializacji, lub przed i po deserializacji obiektu. Atrybuty mogą być stosowane na wszystkich poziomach hierarchii dziedziczenia typu, a każda metoda jest wywoływana w hierarchii od bazy do najbardziej pochodnej. Ten mechanizm pozwala uniknąć złożoności i wszelkich powstających problemów związanych z <xref:System.Runtime.Serialization.ISerializable> implementacją interfejsu przez nadanie odpowiedzialności za serializację i deserializacja do najbardziej pochodnej implementacji. Ponadto ten mechanizm pozwala elementy formatujące do ignorowania populacji pola i pobieranie ze strumienia serializacji. Aby uzyskać szczegółowe informacje i przykłady kontrolowania serializacji i deserializacji, kliknij dowolne z poprzednich linków.  
  
 Ponadto podczas dodawania nowego pola do istniejącego typu możliwego do serializacji należy zastosować <xref:System.Runtime.Serialization.OptionalFieldAttribute> atrybut do pola. <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoruje braku pola podczas przetwarzania strumienia, w którym brakuje nowe pole.  
  
## <a name="implementing-the-iserializable-interface"></a>Implementowanie interfejsu ISerializable  
 Innym sposobem na kontrolowanie serializacji jest osiągnięcie przez implementację <xref:System.Runtime.Serialization.ISerializable> interfejsu w obiekcie. Należy jednak pamiętać, że metoda w poprzedniej sekcji zastępuje tę metodę w celu sterowania serializacji.  
  
 Ponadto nie należy używać serializacji domyślnej dla klasy, która jest oznaczona atrybutem [Serializable](xref:System.SerializableAttribute) i ma deklaratywne lub bezwzględne zabezpieczenia na poziomie klasy lub w konstruktorach. Zamiast tego te klasy powinny zawsze implementować <xref:System.Runtime.Serialization.ISerializable> interfejs.  
  
 Implementacja <xref:System.Runtime.Serialization.ISerializable> obejmuje implementację `GetObjectData` metody i konstruktora specjalnego, który jest używany podczas deserializacji obiektu. Poniższy przykładowy kod przedstawia sposób implementacji <xref:System.Runtime.Serialization.ISerializable> na `MyObject` klasie z poprzedniej sekcji.  
  
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
  
 Gdy **GetObjectData** jest wywoływana podczas serializacji, użytkownik jest odpowiedzialny za wypełnienie <xref:System.Runtime.Serialization.SerializationInfo> dostarczonego z wywołaniem metody. Dodaj serializowana jako pary nazw i wartości zmiennych. Tekst może służyć jako nazwę. Możesz zdecydować, które zmienne składowe są dodawane do <xref:System.Runtime.Serialization.SerializationInfo>, pod warunkiem, że seializowane jest wystarczająco dużo danych, by można było przywrócić obiekt podczas deserializacji. Klasy pochodne powinny wywoływać metodę **GetObjectData** w obiekcie podstawowym, jeśli ta ostatnia implementuje <xref:System.Runtime.Serialization.ISerializable>.  
  
 Należy zauważyć, że serializacji może pozwalać na inny kod, aby wyświetlić lub zmodyfikować dane wystąpienia obiektu, który jest niedostępny. W związku z tym kod, który wykonuje [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) serializacji, wymaga <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> SecurityPermission z określoną flagą. W obszarze domyślne zasady to uprawnienie nie zostanie podany, do pobieranych przez Internet lub z intranetu kod; to uprawnienie udziela się tylko kod na komputerze lokalnym. Metoda **GetObjectData** musi być jawnie chroniona przez wymaganie [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z określoną <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagą lub przez zajęcie innych uprawnień, które w sposób chroniący dane prywatne.  
  
 Jeśli pole prywatne przechowuje poufne informacje, należy uzyskać odpowiednie uprawnienia w witrynie **GetObjectData** w celu ochrony danych. Należy pamiętać, że kod, który został przyznany [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z określoną flagą **SerializationFormatter** , może wyświetlać i modyfikować dane przechowywane w polach prywatnych. Złośliwy obiekt wywołujący, który udzielił tej [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) , może wyświetlać dane, takie jak ukryte Lokalizacje katalogów lub przyznane uprawnienia, a następnie używać danych w celu wykorzystania luki w zabezpieczeniach na komputerze. Aby uzyskać pełną listę flag uprawnień zabezpieczeń, które można określić, zobacz [Wyliczenie SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).  
  
 Należy zastanowić się, że <xref:System.Runtime.Serialization.ISerializable> kiedy jest dodawany do klasy, należy zaimplementować zarówno **GetObjectData** , jak i specjalny Konstruktor. Kompilator wyświetli ostrzeżenie, jeśli brakuje **GetObjectData** . Jednak ponieważ nie można wymusić implementacji konstruktora, nie są wyświetlane żadne ostrzeżenia, jeśli Konstruktor jest nieobecny, a wyjątek jest zgłaszany podczas próby deserializacji klasy bez konstruktora.  
  
 Bieżący projekt został favored powyżej <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> metodę w celu obejściu potencjalne problemy dotyczące zabezpieczeń i przechowywania wersji. Na przykład `SetObjectData` Metoda musi być publiczna, jeśli jest zdefiniowana jako część interfejsu; w ten sposób użytkownicy muszą napisać kod w celu obrony przed przypisaniem metody **SetObjectData** wiele razy. W przeciwnym razie złośliwa aplikacja wywołująca metodę **SetObjectData** na obiekcie w procesie wykonywania operacji może spowodować potencjalne problemy.  
  
 Podczas deserializacji <xref:System.Runtime.Serialization.SerializationInfo> została przekazana do klasy za pomocą konstruktora przewidzianej do tego celu. Wszelkie ograniczenia widoczności umieszczone na Konstruktorze są ignorowane, gdy obiekt jest deserializowany; można oznaczyć klasę jako publiczną, chronioną, wewnętrzną lub prywatną. Jednak jest najlepszym rozwiązaniem, aby chronione, chyba że klasa jest zapieczętowany, w takim przypadku konstruktora powinien być oznaczony prywatnych konstruktora. Konstruktor również należy wykonać dokładne sprawdzenie poprawności danych wejściowych. Aby uniknąć nieprawidłowego użycia przez złośliwego kodu, konstruktora powinien wymuszać taką samą kontroli bezpieczeństwa i uprawnienia wymagane do uzyskania wystąpienie klasy za pomocą dowolnego innego konstruktora. Jeśli nie przestrzegasz tego zalecenia, złośliwy kod może preserializować obiekt, uzyskać kontrolę z [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) z określoną <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flagą i deserializować obiekt na komputerze klienckim, pomijając wszelkie zabezpieczenia, które zostałyby zastosowane podczas konstruowania wystąpienia standardowego przy użyciu konstruktora publicznego.  
  
 Aby przywrócić stan obiektu, po prostu Pobierz wartości zmiennych z <xref:System.Runtime.Serialization.SerializationInfo> używania nazw używanych podczas serializacji. Jeśli klasa bazowa implementuje <xref:System.Runtime.Serialization.ISerializable>, Konstruktor podstawowy powinien zostać wywołany, aby umożliwić obiektowi bazowemu przywrócenie zmiennych.  
  
 Podczas wyprowadzania nowej klasy z klasy, która implementuje <xref:System.Runtime.Serialization.ISerializable>, Klasa pochodna musi implementować zarówno konstruktora, jak i metodę **GetObjectData** , jeśli ma zmienne, które muszą być serializowane. Poniższy przykład kodu pokazuje, jak to zrobić, `MyObject` przy użyciu klasy pokazanej wcześniej.  
  
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
  
 Nie zapomnij wywołać klasy bazowej w konstruktorze deserializacji. Jeśli to nie zrobisz, Konstruktor w klasie bazowej nigdy nie zostanie wywołany, a obiekt nie jest w pełni skonstruowany po deserializacji.  
  
 Obiekty są odtworzone wewnątrz i wywołania metody podczas deserializacji może mieć niepożądane skutki uboczne, ponieważ metody o nazwie może odnosić się do odwołuje się do obiektu, które nie została przeprowadzona przez razem, gdy zostanie nawiązane połączenie. Jeśli deserializowana Klasa implementuje <xref:System.Runtime.Serialization.IDeserializationCallback> <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%2A> metodę, metoda jest wywoływana automatycznie, gdy zostanie odszeregowany cały Graf obiektu. Na tym etapie wszystkie obiekty podrzędne, do których odwołuje się zostały w pełni przywrócone. Tablica skrótów jest typowym przykładem klasy, która jest trudna do deserializacji bez użycia odbiornika zdarzeń. Łatwo można pobrać par kluczy i wartości podczas deserializacji, ale dodanie tych obiektów do tabeli mieszania może spowodować problemy, ponieważ nie ma żadnej gwarancji tej klasy, które opracowane na podstawie tabeli mieszania deserializacji. Wywołanie metody w tabeli mieszania na tym etapie z tego powodu nie jest zalecane.  
  
## <a name="see-also"></a>Zobacz też

- [Serializacja binarna](binary-serialization.md)
- [Serializacja XML i SOAP](xml-and-soap-serialization.md)
- [Zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md)
