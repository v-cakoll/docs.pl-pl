---
title: Domyślny marshaling dla obiektów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: e0de715a3ed33eedf212fc3e0e9930c9cbaa0a38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123591"
---
# <a name="default-marshaling-for-objects"></a>Domyślny marshaling dla obiektów

Parametry i pola, które <xref:System.Object?displayProperty=nameWithType> zostały wpisane jako mogą być ujawnione w kodzie niezarządzanym jako jeden z następujących typów:

- Wariant, gdy obiekt jest parametrem.

- Interfejs, gdy obiekt jest polem struktury.

Tylko usługa międzyoperacyjna modelu COM obsługuje kierowanie dla typów obiektów. Domyślnym zachowaniem jest kierowanie obiektów do wariantów COM. Te reguły mają zastosowanie tylko do **obiektu** typu i nie mają zastosowania do obiektów silnie wpisanych, które pochodzą z klasy **Object** .

## <a name="marshaling-options"></a>Opcje organizowania

W poniższej tabeli przedstawiono opcje organizowania dla typu danych **obiekt** . Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania obiektów.

|Typ wyliczenia|Opis niezarządzanego formatu|
|----------------------|-------------------------------------|
|**UnmanagedType. struct**<br /><br /> (domyślnie dla parametrów)|Wariant w stylu COM.|
|**UnmanagedType. Interface**|Interfejs **IDispatch** , o ile to możliwe; w przeciwnym razie interfejs **IUnknown** .|
|**UnmanagedType. IUnknown**<br /><br /> (domyślnie dla pól)|Interfejs **IUnknown** .|
|**UnmanagedType. IDispatch**|Interfejs **IDispatch** .|

W poniższym przykładzie przedstawiono definicję interfejsu zarządzanego dla programu `MarshalObject`.

```vb
Interface MarshalObject
   Sub SetVariant(o As Object)
   Sub SetVariantRef(ByRef o As Object)
   Function GetVariant() As Object

   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _
      As Object)
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _
      As Object)
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object
End Interface
```

```csharp
interface MarshalObject {
   void SetVariant(Object o);
   void SetVariantRef(ref Object o);
   Object GetVariant();

   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();
}
```

Poniższy kod eksportuje `MarshalObject` interfejs do biblioteki typów.

```cpp
interface MarshalObject {
   HRESULT SetVariant([in] VARIANT o);
   HRESULT SetVariantRef([in,out] VARIANT *o);
   HRESULT GetVariant([out,retval] VARIANT *o)
   HRESULT SetIDispatch([in] IDispatch *o);
   HRESULT SetIDispatchRef([in,out] IDispatch **o);
   HRESULT GetIDispatch([out,retval] IDispatch **o)
   HRESULT SetIUnknown([in] IUnknown *o);
   HRESULT SetIUnknownRef([in,out] IUnknown **o);
   HRESULT GetIUnknown([out,retval] IUnknown **o)
}
```

> [!NOTE]
> Organizator międzyoperacyjny automatycznie zwalnia wszelki przydzielony obiekt wewnątrz wariantu po wywołaniu.

Poniższy przykład przedstawia sformatowany typ wartości.

```vb
Public Structure ObjectHolder
   Dim o1 As Object
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object
End Structure
```

```csharp
public struct ObjectHolder {
   Object o1;
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;
}
```

Poniższy kod eksportuje sformatowany typ do biblioteki typów.

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a>Kierowanie obiektu do interfejsu

Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejsem klasy dla zarządzanego typu <xref:System.Object> ( **_object** interfejs). Ten interfejs jest wpisywany jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) lub **IUnknown** (**UnmanagedType. IUnknown**) w bibliotece typów będących wynikiem. Klienci modelu COM mogą dynamicznie wywoływać elementy członkowskie zarządzanej klasy lub wszelkich członków wdrożonych przez klasy pochodne za pomocą interfejsu **_object** . Klient może również wywołać metodę **QueryInterface** , aby uzyskać inny interfejs jawnie zaimplementowany przez typ zarządzany.

## <a name="marshaling-object-to-variant"></a>Kierowanie obiektu do wariantu

Gdy obiekt jest zorganizowany do wariantu, wewnętrzny typ Variant jest określany w czasie wykonywania na podstawie następujących reguł:

- Jeśli odwołanie do obiektu ma wartość null (**Nothing** w Visual Basic), obiekt jest zorganizowany do wariantu typu **VT_EMPTY**.

- Jeśli obiekt jest wystąpieniem dowolnego typu wymienionych w poniższej tabeli, wynikowy typ Variant jest określany przez reguły wbudowane w organizatora i pokazane w tabeli.

- Inne obiekty, które muszą jawnie kontrolować zachowanie organizowania, mogą implementować <xref:System.IConvertible> interfejs. W takim przypadku typ Variant jest określany przez kod typu zwracany przez <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metodę. W przeciwnym razie obiekt jest zorganizowany jako wariant typu **VT_UNKNOWN**.

### <a name="marshaling-system-types-to-variant"></a>Kierowanie typów systemu do wariantu

W poniższej tabeli przedstawiono typy obiektów zarządzanych i odpowiadające im typy wariantów COM. Te typy są konwertowane tylko wtedy, gdy podpis wywoływanej metody jest typu <xref:System.Object?displayProperty=nameWithType>.

|Typ obiektu|Typ Variant COM|
|-----------------|----------------------|
|Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).|**VT_EMPTY**|
|<xref:System.DBNull?displayProperty=nameWithType>|**VT_NULL**|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|**VT_ERROR**|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|**VT_ERROR** z **E_PARAMNOTFOUND**|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|**VT_DISPATCH**|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|**VT_UNKNOWN**|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|**VT_CY**|
|<xref:System.Boolean?displayProperty=nameWithType>|**VT_BOOL**|
|<xref:System.SByte?displayProperty=nameWithType>|**VT_I1**|
|<xref:System.Byte?displayProperty=nameWithType>|**VT_UI1**|
|<xref:System.Int16?displayProperty=nameWithType>|**VT_I2**|
|<xref:System.UInt16?displayProperty=nameWithType>|**VT_UI2**|
|<xref:System.Int32?displayProperty=nameWithType>|**VT_I4**|
|<xref:System.UInt32?displayProperty=nameWithType>|**VT_UI4**|
|<xref:System.Int64?displayProperty=nameWithType>|**VT_I8**|
|<xref:System.UInt64?displayProperty=nameWithType>|**VT_UI8**|
|<xref:System.Single?displayProperty=nameWithType>|**VT_R4**|
|<xref:System.Double?displayProperty=nameWithType>|**VT_R8**|
|<xref:System.Decimal?displayProperty=nameWithType>|**VT_DECIMAL**|
|<xref:System.DateTime?displayProperty=nameWithType>|**VT_DATE**|
|<xref:System.String?displayProperty=nameWithType>|**VT_BSTR**|
|<xref:System.IntPtr?displayProperty=nameWithType>|**VT_INT**|
|<xref:System.UIntPtr?displayProperty=nameWithType>|**VT_UINT**|
|<xref:System.Array?displayProperty=nameWithType>|**VT_ARRAY**|

Korzystając z `MarshalObject` interfejsu zdefiniowanego w poprzednim przykładzie, Poniższy przykład kodu demonstruje, jak przekazać różne typy wariantów do serwera com.

```vb
Dim mo As New MarshalObject()
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.
```

```csharp
MarshalObject mo = new MarshalObject();
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.
```

Typy com, które nie mają odpowiednich typów zarządzanych, mogą być organizowane przy użyciu klas otoki <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>takich <xref:System.Runtime.InteropServices.UnknownWrapper>jak, <xref:System.Runtime.InteropServices.CurrencyWrapper>, i. Poniższy przykład kodu demonstruje, jak używać tych otok do przekazywania różnych typów wariantów do serwera COM.

```vb
Imports System.Runtime.InteropServices
' Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(New UnknownWrapper(inew))
' Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(New DispatchWrapper(inew))
' Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(New ErrorWrapper(&H80054002))
' Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))
```

```csharp
using System.Runtime.InteropServices;
// Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(new UnknownWrapper(inew));
// Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(new DispatchWrapper(inew));
// Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(new ErrorWrapper(0x80054002));
// Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));
```

Klasy otoki są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.

### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Kierowanie interfejsu obiektem IConvertible do wariantu

Typy inne niż wymienione w poprzedniej sekcji mogą kontrolować sposób, w jaki są one organizowane przez implementację <xref:System.IConvertible> interfejsu. Jeśli obiekt implementuje interfejs **obiektem IConvertible** , typ Variant com jest określany w czasie wykonywania przez wartość <xref:System.TypeCode> wyliczenia zwracanego z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.

W poniższej tabeli przedstawiono możliwe wartości wyliczenia elementu **TypeCode** i odpowiedni typ modelu COM dla każdej wartości.

|Elementu TypeCode|Typ Variant COM|
|--------------|----------------------|
|**TypeCode. Empty**|**VT_EMPTY**|
|**TypeCode. Object**|**VT_UNKNOWN**|
|**TypeCode. DBNull**|**VT_NULL**|
|**TypeCode. Boolean**|**VT_BOOL**|
|**TypeCode. Char**|**VT_UI2**|
|**TypeCode. nadana**|**VT_I1**|
|**TypeCode. Byte**|**VT_UI1**|
|**TypeCode. Int16**|**VT_I2**|
|**TypeCode. UInt16**|**VT_UI2**|
|**TypeCode. Int32**|**VT_I4**|
|**TypeCode. UInt32**|**VT_UI4**|
|**TypeCode. Int64**|**VT_I8**|
|**TypeCode. UInt64**|**VT_UI8**|
|**TypeCode. Single**|**VT_R4**|
|**TypeCode. Double**|**VT_R8**|
|**TypeCode. Decimal**|**VT_DECIMAL**|
|**TypeCode. DateTime**|**VT_DATE**|
|**TypeCode. String**|**VT_BSTR**|
|Bez pomocy technicznej.|**VT_INT**|
|Bez pomocy technicznej.|**VT_UINT**|
|Bez pomocy technicznej.|**VT_ARRAY**|
|Bez pomocy technicznej.|**VT_RECORD**|
|Bez pomocy technicznej.|**VT_CY**|
|Bez pomocy technicznej.|**VT_VARIANT**|

Wartość wariantu COM jest określana przez wywołanie interfejsu typu **IConvertible.to** *Type* , gdzie **do** *typu* jest procedura konwersji odpowiadająca typowi zwróconemu z **obiektem IConvertible. GetTypeCode**. Na przykład obiekt, który zwraca element **TypeCode. Double** z **obiektem IConvertible. GetTypeCode** jest zorganizowany jako wariant modelu COM typu **VT_R8**. Można uzyskać wartość wariantu (przechowywaną w polu **dblVal** wariantu com) przez rzutowanie do interfejsu **obiektem IConvertible** i wywołanie <xref:System.IConvertible.ToDouble%2A> metody.

## <a name="marshaling-variant-to-object"></a>Kierowanie elementu Variant do obiektu

Podczas organizowania elementu Variant z obiektem, typu i czasami wartość, z której jest zorganizowany, określa typ utworzonego obiektu. W poniższej tabeli przedstawiono każdy typ wariantu i odpowiedni typ obiektu, który organizator tworzy, gdy wariant jest przekazywany z modelu COM do .NET Framework.

|Typ Variant COM|Typ obiektu|
|----------------------|-----------------|
|**VT_EMPTY**|Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).|
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|
|**VT_DISPATCH**|**System. __ComObject** lub null, if (pdispVal = = null)|
|**VT_UNKNOWN**|**System. __ComObject** lub null, if (punkVal = = null)|
|**VT_ERROR**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_BOOL**|<xref:System.Boolean?displayProperty=nameWithType>|
|**VT_I1**|<xref:System.SByte?displayProperty=nameWithType>|
|**VT_UI1**|<xref:System.Byte?displayProperty=nameWithType>|
|**VT_I2**|<xref:System.Int16?displayProperty=nameWithType>|
|**VT_UI2**|<xref:System.UInt16?displayProperty=nameWithType>|
|**VT_I4**|<xref:System.Int32?displayProperty=nameWithType>|
|**VT_UI4**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_I8**|<xref:System.Int64?displayProperty=nameWithType>|
|**VT_UI8**|<xref:System.UInt64?displayProperty=nameWithType>|
|**VT_R4**|<xref:System.Single?displayProperty=nameWithType>|
|**VT_R8**|<xref:System.Double?displayProperty=nameWithType>|
|**VT_DECIMAL**|<xref:System.Decimal?displayProperty=nameWithType>|
|**VT_DATE**|<xref:System.DateTime?displayProperty=nameWithType>|
|**VT_BSTR**|<xref:System.String?displayProperty=nameWithType>|
|**VT_INT**|<xref:System.Int32?displayProperty=nameWithType>|
|**VT_UINT**|<xref:System.UInt32?displayProperty=nameWithType>|
|**VT_ARRAY** &#124; **VT_**\*|<xref:System.Array?displayProperty=nameWithType>|
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|
|**VT_RECORD**|Odpowiedni opakowany typ wartości.|
|**VT_VARIANT**|Bez pomocy technicznej.|

Typy wariantów przesyłane z modelu COM do kodu zarządzanego, a następnie z powrotem do modelu COM mogą nie zachować tego samego typu wariantu dla czasu trwania wywołania. Należy wziąć pod uwagę to, co się stanie, gdy wariant typu **VT_DISPATCH** jest przenoszona z modelu COM do .NET Framework. Podczas organizowania wariant jest konwertowany na <xref:System.Object?displayProperty=nameWithType>. Jeśli **obiekt** jest następnie przekazywany z powrotem do modelu COM, jest on zorganizowany z powrotem do wariantu typu **VT_UNKNOWN**. Nie ma gwarancji, że wariant utworzony, gdy obiekt jest zorganizowany z kodu zarządzanego do modelu COM, będzie tego samego typu co wariant użyty początkowo do utworzenia obiektu.

## <a name="marshaling-byref-variants"></a>Kierowanie wariantów ByRef

Chociaż warianty mogą być przesyłane przez wartość lub przez odwołanie, flaga **VT_BYREF** może być również używana z dowolnym typem VARIANT, aby wskazać, że zawartość wariantu jest przesyłana przez odwołanie, a nie przez wartość. Różnica między organizowaniem wariantów według odwołania i kierowaniem wariantów z zestawem flag **VT_BYREF** może być myląca. Na poniższej ilustracji objaśniono różnice:

![Diagram pokazujący wariant zakończony przez stos.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)
Warianty przenoszone przez wartość i przez odwołanie

**Domyślne zachowanie dla organizowania obiektów i wariantów według wartości**

- Podczas przekazywania obiektów z kodu zarządzanego do modelu COM zawartość obiektu jest kopiowana do nowego wariantu utworzonego przez organizatora przy użyciu reguł zdefiniowanych w [kierowaniu obiektu do wariantu](#marshaling-object-to-variant). Zmiany wprowadzone do wariantu po stronie niezarządzanej nie są propagowane z powrotem do oryginalnego obiektu po powrocie z wywołania.

- Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariantu jest kopiowana do nowo utworzonego obiektu, przy użyciu reguł zdefiniowanych w [kierowaniu wariantu do obiektu](#marshaling-variant-to-object). Zmiany wprowadzone do obiektu na stronie zarządzanej nie są propagowane z powrotem do oryginalnego wariantu w przypadku powrotu z wywołania.

**Domyślne zachowanie dla organizowania obiektów i wariantów według odwołania**

Aby propagować zmiany z powrotem do obiektu wywołującego, parametry muszą być przesyłane przez odwołanie. Można na przykład użyć słowa kluczowego **ref** w języku C# (lub **ByRef** w Visual Basic kodzie zarządzanym) do przekazywania parametrów przez odwołanie. W modelu COM parametry odwołania są przesyłane przy użyciu wskaźnika, takiego jak **Variant \* **.

- Podczas przekazywania obiektu do modelu COM przez odwołanie organizator tworzy nowy wariant i kopiuje zawartość odwołania do obiektu do wariantu przed wywołaniem. Wariant jest przesyłany do niezarządzanej funkcji, w której użytkownik może zmienić zawartość wariantu. W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do wariantu po stronie niezarządzanej są propagowane do oryginalnego obiektu. Jeśli Typ wariantu różni się od typu wariantu przekazanego do wywołania, zmiany są propagowane z powrotem do obiektu innego typu. Oznacza to, że typ obiektu, który został przesłany do wywołania może różnić się od typu obiektu zwróconego przez wywołanie.

- Podczas przekazywania wariantu do kodu zarządzanego przez odwołanie organizator tworzy nowy obiekt i kopiuje zawartość wariantu do obiektu przed wywołaniem. Odwołanie do obiektu jest przesyłane do funkcji zarządzanej, gdzie użytkownik może zmienić obiekt. W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do przywoływanego obiektu są propagowane z powrotem do oryginalnego wariantu. Jeśli typ obiektu różni się od typu obiektu przekazanego do wywołania, typ oryginalnego wariantu zostanie zmieniony, a wartość jest propagowana z powrotem do wariantu. Ponownie Typ wariantu przekazana do wywołania może różnić się od typu wariantu zwróconego przez wywołanie.

 **Domyślne zachowanie organizowania wariantu z ustawioną flagą VT_BYREF**

- Wariant, który jest przesyłany do kodu zarządzanego przez wartość, może mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera odwołanie zamiast wartości. W takim przypadku wariant jest nadal kierowany do obiektu, ponieważ wariant jest przekazywany przez wartość. Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem. Obiekt jest następnie przekazywać do zarządzanej funkcji; Jednak po powrocie z wywołania obiekt nie jest propagowany z powrotem do oryginalnego wariantu. Zmiany wprowadzone w obiekcie zarządzanym zostaną utracone.

  > [!CAUTION]
  > Nie ma możliwości zmiany wartości wariantu przekazaną przez wartość, nawet jeśli wariant ma ustawioną flagę **VT_BYREF** .

- Wariant jest przesyłany do kodu zarządzanego przez odwołanie może również mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera inne odwołanie. Jeśli tak, wariant jest zorganizowany do obiektu **ref** , ponieważ wariant jest przekazywany przez odwołanie. Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem. W przypadku powrotu z wywołania, wartość obiektu jest propagowana z powrotem do odwołania w obrębie oryginalnego wariantu tylko wtedy, gdy obiekt jest tego samego typu co obiekt przekazane. Oznacza to, że propagacja nie zmienia typu wariantu z ustawioną flagą **VT_BYREF** . Jeśli typ obiektu zostanie zmieniony podczas wywołania, <xref:System.InvalidCastException> występuje po powrocie z wywołania.

Poniższa tabela podsumowuje reguły propagacji dla wariantów i obiektów.

|Z|Do|Zmiany rozpropagowane|
|----------|--------|-----------------------------|
|**Wariant**  *v*|**Obiekt**  *o*|Nigdy|
|**Obiekt**  *o*|**Wariant**  *v*|Nigdy|
|**Wariant wariantów*****\*****pv*     |**Obiekt ref**  *o*|Zawsze|
|**Obiekt ref**  *o*|**Wariant wariantów*****\*****pv*     |Zawsze|
|**Wariant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**|**Obiekt**  *o*|Nigdy|
|**Wariant**  *v* **(VT_BYREF** *&#124;* **VT_)**|**Obiekt ref**  *o*|Tylko wtedy, gdy typ nie został zmieniony.|

## <a name="see-also"></a>Zobacz też

- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
