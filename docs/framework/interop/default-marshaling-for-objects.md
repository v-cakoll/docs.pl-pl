---
title: Organizowanie domyślne dotyczące obiektów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84a3ea24120a9548c9d1cd2b7b83997a2c849cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528028"
---
# <a name="default-marshaling-for-objects"></a>Domyślny marshaling dla obiektów
Parametry i pola wpisanych w formie <xref:System.Object?displayProperty=nameWithType> mogą łączyć się z kodem niezarządzanym jako jeden z następujących typów:  
  
-   Wariant, gdy obiekt jest parametrem.  
  
-   Interfejs, gdy obiekt jest polem struktury.  
  
 Tylko Usługa międzyoperacyjna modelu COM obsługuje marshaling dla typów obiektów. Zachowanie domyślne jest do organizowania obiektów COM wariantów. Te reguły mają zastosowanie tylko do typu **obiektu** i nie mają zastosowania do silnie typizowanych obiektów, które wynikają z **obiektu** klasy.  
  
 Ten temat zawiera następujące informacje dodatkowe na temat marshaling typów obiektów:  
  
-   [Marshaling opcje](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [Kierowanie obiektu na interfejs](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [Marshalingu obiektu Variant](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [Marshaling wariant do obiektu](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [Marshaling wariantów ByRef](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a>Marshaling opcje  
 W poniższej tabeli przedstawiono opcje kierowania **obiektu** typu danych. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> obiektów marshal wartości wyliczenia.  
  
|Typ wyliczeniowy|Opis formatu niezarządzanych|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (ustawienie domyślne dla parametrów)|Wariant styl modelu COM.|  
|**UnmanagedType.Interface**|**IDispatch** interfejsu, jeśli jest to możliwe; w przeciwnym razie **IUnknown** interfejsu.|  
|**UnmanagedType.IUnknown**<br /><br /> (ustawienie domyślne dla pól)|**IUnknown** interfejsu.|  
|**UnmanagedType.IDispatch**|**IDispatch** interfejsu.|  
  
 Poniższy przykład przedstawia definicję interfejsu zarządzanych `MarshalObject`.  
  
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
  
 Poniższy kod eksporty `MarshalObject` interfejsu do biblioteki typów.  
  
```  
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
>  Organizator międzyoperacyjny automatycznie zwalnia wszelkie przydzielonego obiektu wewnątrz wariant po wywołaniu.  
  
 Poniższy przykład pokazuje typ sformatowanej wartości.  
  
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
  
 Poniższy kod umożliwia wyeksportowanie sformatowane typu do biblioteki typów.  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a>Kierowanie obiektu na interfejs  
 Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejs klasy typu zarządzanego <xref:System.Object> ( **_obiekt** interfejsu). Ten interfejs jest wpisana jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) lub **IUnknown** (**UnmanagedType.IUnknown**) w wynikowej biblioteki typów. Klienci COM dynamicznie wywołać członków klasy zarządzanej lub członków implementowany przez jej klasy pochodne za pośrednictwem **_obiekt** interfejsu. Klienta można również wywołać **QueryInterface** do uzyskania innych interfejsu jawnie implementowana przez typ zarządzany.  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a>Marshalingu obiektu Variant  
 Gdy obiekt jest przekazywany do typu variant, wewnętrzny typ wariantu jest określana w czasie wykonywania, na podstawie następujących reguł:  
  
-   Jeśli odwołanie do obiektu ma wartość null (**nic** w języku Visual Basic), obiekt jest przekazywany do wariant typu **VT_EMPTY**.  
  
-   Jeśli obiekt jest wystąpieniem typu wymienione w poniższej tabeli, wynikowy typ wariantu zależy od reguł wbudowanych w organizator i wyświetlane w tabeli.  
  
-   Inne obiekty, które należy jawnie kontrolować zachowanie marshalingu można zaimplementować <xref:System.IConvertible> interfejsu. W takim przypadku typ wariantu zależy od kodu typ zwracany z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody. W przeciwnym razie, obiekt jest organizowana jako wariant typu **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Marshaling System typów Variant  
 W poniższej tabeli przedstawiono typy obiektów zarządzanych oraz odpowiadające typy variant COM. Te typy są konwertowane tylko wtedy, gdy podpis metody wywołanego typu <xref:System.Object?displayProperty=nameWithType>.  
  
|Typ obiektu|Typ wariantu COM|  
|-----------------|----------------------|  
|Wartość null, odwołanie do obiektu (**nic** w języku Visual Basic).|**VT_EMPTY**|  
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
  
 Za pomocą `MarshalObject` interfejsem zdefiniowanym w poprzednim przykładzie, w poniższym przykładzie kodu pokazano, jak przekazać różnego rodzaju wariantów do serwera COM.  
  
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
  
 Może być organizowany typy modelu COM, które nie mają odpowiednich typów zarządzanych przy użyciu klasy otoki, takich jak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, i <xref:System.Runtime.InteropServices.CurrencyWrapper>. Poniższy przykład kodu pokazuje, jak przekazać różnego rodzaju wariantów do serwera COM za pomocą te otoki.  
  
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
  
 Klasy otok są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Organizowanie interfejsu IConvertible Variant  
 Typy inne niż te wymienione w poprzedniej sekcji można kontrolować, jak są organizowane przez zaimplementowanie <xref:System.IConvertible> interfejsu. Jeśli obiekt implementuje **IConvertible** interfejs, typ wariantu COM jest ustalany w czasie wykonywania wartość <xref:System.TypeCode> wyliczenie zwróciło <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.  
  
 W poniższej tabeli przedstawiono możliwe wartości **elementu TypeCode** wyliczenie i odpowiedni typ wariantu COM dla każdej wartości.  
  
|TypeCode|Typ wariantu COM|  
|--------------|----------------------|  
|**TypeCode.Empty**|**VT_EMPTY**|  
|**TypeCode.Object**|**VT_UNKNOWN**|  
|**TypeCode.DBNull**|**VT_NULL**|  
|**TypeCode.Boolean**|**VT_BOOL**|  
|**TypeCode.Char**|**VT_UI2**|  
|**TypeCode.Sbyte**|**VT_I1**|  
|**TypeCode.Byte**|**VT_UI1**|  
|**TypeCode.Int16**|**VT_I2**|  
|**TypeCode.UInt16**|**VT_UI2**|  
|**TypeCode.Int32**|**VT_I4**|  
|**TypeCode.UInt32**|**VT_UI4**|  
|**TypeCode.Int64**|**VT_I8**|  
|**TypeCode.UInt64**|**VT_UI8**|  
|**TypeCode.Single**|**VT_R4**|  
|**TypeCode.Double**|**VT_R8**|  
|**TypeCode.Decimal**|**VT_DECIMAL**|  
|**TypeCode.DateTime**|**VT_DATE**|  
|**TypeCode.String**|**VT_BSTR**|  
|Nieobsługiwane.|**VT_INT**|  
|Nieobsługiwane.|**VT_UINT**|  
|Nieobsługiwane.|**VT_ARRAY**|  
|Nieobsługiwane.|**VT_RECORD**|  
|Nieobsługiwane.|**VT_CY**|  
|Nieobsługiwane.|**VT_VARIANT**|  
  
 Wartość wariantu COM jest określana przez wywołanie metody **IConvertible.To** *typu* interfejsu, gdzie **do** *typu* jest konwersja Procedura, która odnosi się do typu, który został zwrócony z **IConvertible.GetTypeCode**. Na przykład, obiekt, który zwraca **TypeCode.Double** z **IConvertible.GetTypeCode** jest organizowana jako wariant COM typu **VT_R8**. Można uzyskać wartość wariantu (przechowywane w **dblVal** pole wariant COM) przez rzutowanie do **IConvertible** interfejsu i wywoływania <xref:System.IConvertible.ToDouble%2A> metody.  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a>Marshaling wariant do obiektu  
 Generowane po marshaling wariant do obiektu, typ i czasami wartość wariantu zorganizowanej Określa typ obiektu. W poniższej tabeli przedstawiono każdy typ wariantu i odpowiedni typ obiektu, tworzącą Organizator, gdy wariant jest przekazywany z modelu COM do programu .NET Framework.  
  
|Typ wariantu COM|Typ obiektu|  
|----------------------|-----------------|  
|**VT_EMPTY**|Wartość null, odwołanie do obiektu (**nic** w języku Visual Basic).|  
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|  
|**VT_DISPATCH**|**.__ComObject** lub wartość null, jeśli (pdispVal == wartość null)|  
|**VT_UNKNOWN**|**.__ComObject** lub wartość null, jeśli (punkVal == wartość null)|  
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
|**VT_ARRAY** &AMP;#124; **VT_**\*|<xref:System.Array?displayProperty=nameWithType>|  
|**VT_CY**|<xref:System.Decimal?displayProperty=nameWithType>|  
|**VT_RECORD**|Odpowiadające opakowanym typem wartościowym.|  
|**VT_VARIANT**|Nieobsługiwane.|  
  
 Typów Variant przekazywane z modelu COM do kodu zarządzanego, a następnie powrót do COM mogą nie zawierać tego samego typu variant na czas trwania wywołania. Należy wziąć pod uwagę, co się stanie po wariant typu **VT_DISPATCH** jest przekazywany z modelu COM do programu .NET Framework. Podczas przekazywania międzyprocesowego, wariant jest konwertowany na <xref:System.Object?displayProperty=nameWithType>. Jeśli **obiektu** jest następnie przekazywany do modelu COM, jest przekazywany do wariant typu **VT_UNKNOWN**. Nie ma żadnej gwarancji, że wariant generowana, gdy obiekt jest przekazywany z kodu zarządzanego w modelu COM będzie tego samego typu jako wariant początkowo użyta do wyprodukowania obiektu.  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a>Marshaling wariantów ByRef  
 Mimo że wariantów sami mogą być przekazywane przez wartość lub przez odwołanie, **VT_BYREF** flagi również można używać z dowolnego typu variant do wskazania, że zawartość wariant są przekazywany przez odwołanie, a nie przez wartość. Różnica między organizowania wariantów przez odwołanie i organizowanie wariant z **VT_BYREF** ustawioną flagą może być mylące. Na poniższej ilustracji wyjaśnia różnice.  
  
 ![Wariant przekazywane na stosie](./media/interopvariant.gif "interopvariant")  
Warianty przekazywane według wartości i według odwołania  
  
 **Domyślne zachowanie w przypadku kierowania obiektami i wariantów według wartości**  
  
-   Przy przekazywaniu obiektów z kodu zarządzanego w modelu COM, zawartość obiektu są kopiowane do nowy wariant utworzone przez organizatora przy użyciu reguł zdefiniowanych w [Marshalingu obiektu Variant](#cpcondefaultmarshalingforobjectsanchor3). Zmiany wprowadzone do wariantu w niezarządzanym nie są propagowane do oryginalnego obiektu na powrót z wywołania.  
  
-   Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariant są kopiowane do nowo utworzonego obiektu przy użyciu reguł zdefiniowanych w [Marshaling wariant obiektowi](#cpcondefaultmarshalingforobjectsanchor4). Zmiany wprowadzone do obiektu zarządzanego stronie nie są propagowane do oryginalnego wariant na powrót z wywołania.  
  
 **Domyślne zachowanie w przypadku kierowania obiektami i wariantów przez odwołanie**  
  
 Propagowanie zmian obiektu wywołującego, parametry muszą być przekazywane przez odwołanie. Na przykład, można użyć **ref** — słowo kluczowe w C# (lub **ByRef** kodu zarządzanego w języku Visual Basic) do przekazania parametrów poprzez odniesienie. W modelu COM, parametry odwołania są przekazywane za pomocą wskaźnika, takich jak **wariant \*** .  
  
-   Podczas przekazywania obiektu dla modelu COM przez odwołanie, organizator tworzy nowy wariant i kopiuje zawartość odwołanie do obiektu do wariant, zanim zostanie nawiązane połączenie. Wariant jest przekazywany do niezarządzanej funkcji, w których użytkownik będzie mógł zmienić zawartość wariant. Na powrót z wywołania wszelkie zmiany wprowadzone do wariantu w niezarządzanym jest propagowany z powrotem do oryginalnego obiektu. Jeśli typ variant różni się od typu variant, podawaną do wywołania, zmiany są propagowane do obiektu innego typu. Oznacza to, że typ obiektu przekazanego do wywołania mogą się różnić od typu Obiekt zwrócony z wywołania.  
  
-   Przy przekazywaniu wariant z kodem zarządzanym przez odwołanie, organizator tworzy nowy obiekt i kopiuje zawartość wariant do obiektu, przed wykonaniem wywołania. Odwołanie do obiektu jest przekazywany do funkcji zarządzanej, gdzie użytkownik jest bezpłatna do zmiany obiektu. Na powrót z wywołania wszelkie zmiany wprowadzone do przywoływanego obiektu jest propagowany z powrotem do oryginalnego wariant. Jeśli typ obiektu różni się od typu obiektu przekazanego do wywołania, typ wariantu, oryginalnym zostanie zmieniony, a wartość jest propagowany z powrotem do wariant. Ponownie typ wariantu przekazane do wywołania mogą się różnić od typu variant, zwrócony z wywołania.  
  
 **Domyślne zachowanie marshalingu wariant z ustawioną flagą VT_BYREF**  
  
-   Wariant został przekazany do kodu zarządzanego przez wartość może mieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołania, a nie wartość. W tym przypadku wariant jest nadal zorganizować do obiektu, ponieważ wariant jest przekazywany przez wartość. Organizator wyłuskań zawartość wariant i automatycznie kopiuje go do nowo utworzonego obiektu przed wykonaniem wywołania. Obiekt jest następnie przekazywany do funkcji zarządzanej; jednak na powrót z wywołania, obiekt nie są propagowane do oryginalnego wariant. Zmiany wprowadzone do obiektu zarządzanego, zostaną utracone.  
  
    > [!CAUTION]
    >  Nie ma sposobu na zmianę wartości przekazywane przez wartość wariantu, nawet wtedy, gdy ma wariant **VT_BYREF** Flaga.  
  
-   Wariant został przekazany do kodu zarządzanego przez odwołanie mogą też istnieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie do innego. Jeśli tak jest, wariant jest przekazywane do **ref** obiektu, ponieważ wariant jest przekazywany przez odwołanie. Organizator wyłuskań zawartość wariant i automatycznie kopiuje go do nowo utworzonego obiektu przed wykonaniem wywołania. Na powrót z wywołania wartość obiektu jest propagowany z powrotem do odwołania w oryginalnym wariant tylko wtedy, gdy obiekt jest tego samego typu, ponieważ obiekt przekazany w. Oznacza to, że propagacja nie zmienia typ zmiennej za pomocą **VT_BYREF** Flaga. Typ obiektu po zmianie podczas wywołania, <xref:System.InvalidCastException> występuje na powrót z wywołania.  
  
 W poniższej tabeli przedstawiono zasady propagacji wariantów i obiektów.  
  
|Z|Zadanie|Zmiany propagowany z powrotem|  
|----------|--------|-----------------------------|  
|**Wariant***v* |**Obiekt***o* |nigdy nie|  
|**Obiekt***o* |**Wariant***v* |nigdy nie|  
|**Variant**  ***\****  *pv*|**Obiekt REF***o* |zawsze|  
|**Obiekt REF***o* |**Variant**  ***\****  *pv*|zawsze|  
|**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**|**Obiekt***o* |nigdy nie|  
|**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**|**Obiekt REF***o* |Tylko wtedy, gdy typ nie uległ zmianie.|  
  
## <a name="see-also"></a>Zobacz także
- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
