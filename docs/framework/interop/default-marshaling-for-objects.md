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
ms.openlocfilehash: 94377fb2079689e7b6af2c94fa24ca2214a5c729
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
---
# <a name="default-marshaling-for-objects"></a>Domyślny marshaling dla obiektów
Parametry i pola typu <xref:System.Object?displayProperty=nameWithType> można wyświetlać do kodu niezarządzanego jako jeden z następujących typów:  
  
-   Wariant, gdy obiekt jest parametrem.  
  
-   Interfejs, gdy obiekt jest polem struktury.  
  
 Tylko Usługa międzyoperacyjna modelu COM obsługuje przekazywanie dla typów obiektów. Domyślnym zachowaniem jest do organizowania obiektów COM Variant. Te reguły dotyczą tylko w typie **obiektu** i nie stosuje się do silnie typizowanych obiektów, które pochodzą z **obiektu** klasy.  
  
 Ten temat zawiera następujące informacje dodatkowe o przekazywanie typów obiektów:  
  
-   [Organizowanie opcje](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [Przekazywanie obiektu na interfejs](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [Kierowanie obiektu do typu Variant](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [Organizowanie Variant do obiektu](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [Organizowanie ByRef Variant](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a>Organizowanie opcje  
 W poniższej tabeli przedstawiono opcje organizowania **obiektu** — typ danych. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie obiektów.  
  
|Typ wyliczenia|Opis formatu niezarządzane|  
|----------------------|-------------------------------------|  
|**UnmanagedType.Struct**<br /><br /> (ustawienie domyślne dla parametrów)|Styl modelu COM variant.|  
|**UnmanagedType.Interface**|**IDispatch** interfejsu, jeśli to możliwe, a w przeciwnym razie **IUnknown** interfejsu.|  
|**UnmanagedType.IUnknown**<br /><br /> (domyślnie dla pola)|**IUnknown** interfejsu.|  
|**UnmanagedType.IDispatch**|**IDispatch** interfejsu.|  
  
 W poniższym przykładzie przedstawiono definicję interfejsu zarządzanego `MarshalObject`.  
  
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
>  Organizator międzyoperacyjnego automatycznie zwalnia dowolnego przydzielonego obiektu wewnątrz wariant po wywołaniu metody.  
  
 W poniższym przykładzie przedstawiono typu sformatowana wartość.  
  
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
  
 Poniższy kod eksportuje sformatowany typu do biblioteki typów.  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a>Przekazywanie obiektu na interfejs  
 Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejs klasy dla typu zarządzanego <xref:System.Object> ( **_Object** interfejs). Ten interfejs jest typu **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) lub **IUnknown** (**UnmanagedType.IUnknown**) w wynikowej biblioteki typów. Klientów modelu COM. można dynamicznie wywołać członkami zarządzanej klasy lub członków implementowane przez jej klas pochodnych za pośrednictwem **_Object** interfejsu. Klient może także wywołać **QueryInterface** uzyskać inny interfejs jawnie implementowana przez typ zarządzany.  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a>Kierowanie obiektu do typu Variant  
 Gdy obiekt jest przekazywane do typu variant, wewnętrzny typ wariantu jest określany w czasie wykonywania na podstawie następujących reguł:  
  
-   Jeśli odwołanie do obiektu ma wartość null (**nic** w języku Visual Basic), obiekt jest przekazywane do wariant typu **VT_EMPTY**.  
  
-   Jeśli obiekt jest wystąpieniem typu wymienione w poniższej tabeli, wynikowy typ wariantu zależy od reguł wbudowanych w organizatora i wyświetlany w tabeli.  
  
-   Inne obiekty, które trzeba jawnie kontrolować zachowanie marshalingu można zaimplementować <xref:System.IConvertible> interfejsu. W takim przypadku typ wariantu jest określany przez kod typ zwrócony z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody. W przeciwnym razie wartość obiektu jest przekazywane jako wariant typu **VT_UNKNOWN**.  
  
### <a name="marshaling-system-types-to-variant"></a>Organizowanie System typów Variant  
 W poniższej tabeli przedstawiono typy zarządzanych obiektów i odpowiednie typy variant modelu COM. Te typy są konwertowane tylko wtedy, gdy podpis metody wywoływanej jest typu <xref:System.Object?displayProperty=nameWithType>.  
  
|Typ obiektu|Typ variant modelu COM|  
|-----------------|----------------------|  
|Odwołanie do obiektu o wartości null (**nic** w języku Visual Basic).|**VT_EMPTY**|  
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
  
 Przy użyciu `MarshalObject` interfejs zdefiniowany w poprzednim przykładzie, w poniższym przykładzie pokazano, jak do przekazania na serwer COM różnego typu Variant.  
  
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
  
 Typy modelu COM, które nie mają odpowiednie typy zarządzane być organizowany przy użyciu klasy otoki, takich jak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, i <xref:System.Runtime.InteropServices.CurrencyWrapper>. Poniższy przykład kodu pokazuje, jak na potrzeby przekazania różnego typu Variant do serwera COM. te otoki.  
  
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
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a>Organizowanie interfejs IConvertible Variant  
 Typów innych niż wymienione w poprzedniej sekcji można kontrolować, jak są przekazywane przez zaimplementowanie <xref:System.IConvertible> interfejsu. Jeśli obiekt implementuje **IConvertible** interfejsu typu variant modelu COM jest określana w czasie wykonywania przez wartość <xref:System.TypeCode> wyliczenie zwrócony z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.  
  
 W poniższej tabeli przedstawiono możliwe wartości **elementu TypeCode** wyliczenie i odpowiedniego typu variant modelu COM dla każdej wartości.  
  
|TypeCode|Typ variant modelu COM|  
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
  
 Wartość variant modelu COM jest określana przez wywołanie metody **IConvertible.To** *typu* interfejsu, gdzie **do** *typu* jest konwersji Procedura umożliwiająca typ, który został zwrócony z **IConvertible.GetTypeCode**. Na przykład obiekt, który zwraca **TypeCode.Double** z **IConvertible.GetTypeCode** jest przekazywane jako typ variant modelu COM typu **VT_R8**. Można uzyskać wartości z wariantu (przechowywane w **dblVal** pole Typ COM variant) przez rzutowanie do **IConvertible** interfejsu i wywoływania <xref:System.IConvertible.ToDouble%2A> — metoda.  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a>Organizowanie Variant do obiektu  
 Gdy organizowanie variant do obiektu, typ i czasami wartość organizowane variant Określa typ obiektu utworzone. W poniższej tabeli przedstawiono każdego typu variant i odpowiedni typ obiektu organizatora tworzy podczas wariant jest przekazywany z modelu COM programu .NET Framework.  
  
|Typ variant modelu COM|Typ obiektu|  
|----------------------|-----------------|  
|**VT_EMPTY**|Odwołanie do obiektu o wartości null (**nic** w języku Visual Basic).|  
|**VT_NULL**|<xref:System.DBNull?displayProperty=nameWithType>|  
|**VT_DISPATCH**|**System.__ComObject** lub wartość null, jeśli (pdispVal == null)|  
|**VT_UNKNOWN**|**System.__ComObject** lub wartość null, jeśli (punkVal == null)|  
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
|**VT_RECORD**|Odpowiadającego opakowanym typem wartościowym.|  
|**VT_VARIANT**|Nieobsługiwane.|  
  
 Typy Variant przekazany z modelu COM do kodu zarządzanego i następnie powrót do modelu COM mogą nie zawierać ten sam typ variant na czas trwania wywołania. Należy rozważyć, co się stanie po wariant typu **VT_DISPATCH** jest przekazywany z modelu COM programu .NET Framework. Podczas przekazywania międzyprocesowego, wariant jest konwertowana na <xref:System.Object?displayProperty=nameWithType>. Jeśli **obiektu** są następnie przekazywane do modelu COM, jest przekazywane do wariant typu **VT_UNKNOWN**. Nie ma żadnej gwarancji, że wariant tworzone, gdy obiekt jest przekazywane z kodu zarządzanego w modelu COM będzie taki sam typ jak variant początkowo używane do tworzenia obiektu.  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a>Organizowanie ByRef Variant  
 Mimo że wariantów same mogą być przekazywane przez wartości lub według odwołania, **VT_BYREF** flagi można również w przypadku każdego typu variant wskazują, że zawartość wariantu są przekazywany przez odwołanie, a nie przez wartość. Różnica między przekazywanie wariantów przez odwołanie i organizowanie wariant z **VT_BYREF** ustawiona flaga może być mylące. Poniższa ilustracja wyjaśnia różnice.  
  
 ![Wariant przekazany na stosie](./media/interopvariant.gif "interopvariant")  
Wariantów przekazywane według wartości i według odwołania  
  
 **Domyślne zachowanie dla organizowanie obiektów i wariantów przez wartość**  
  
-   Podczas przekazywania obiektów z kodu zarządzanego w modelu COM, zawartość obiektu są kopiowane do nowego wariant utworzone przez organizatora, za pomocą reguł zdefiniowanych w [kierowanie obiektu Variant](#cpcondefaultmarshalingforobjectsanchor3). Zmiany wprowadzone do wariantu po stronie niezarządzane nie są propagowane do oryginalnego obiektu na powrót z wywołania.  
  
-   Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariantu są kopiowane do nowo utworzony obiekt, za pomocą reguł zdefiniowanych w [Variant przekazywanie do obiektu](#cpcondefaultmarshalingforobjectsanchor4). Zmiany wprowadzone do obiektu po stronie zarządzanego nie są propagowane do oryginalnego variant na powrót z wywołania.  
  
 **Domyślne zachowanie dla organizowanie obiektów i wariantów przez odwołanie**  
  
 Propagowanie zmian z powrotem na obiekt wywołujący, parametry muszą być przekazywane przez odwołanie. Na przykład można użyć **ref** — słowo kluczowe języka C# (lub **ByRef** kodu zarządzanego w języku Visual Basic) do przekazania parametrów przez odwołanie. W modelu COM, odwołanie parametry są przekazywane, takich jak przy użyciu wskaźnika **variant \*** .  
  
-   Podczas przekazywania obiektu w modelu COM przez odwołanie, organizatora tworzy nowy typ variant i kopiuje zawartość odwołanie obiektu do variant, przed dokonaniem wywołania. Wariant jest przekazywany do funkcji niezarządzanej, gdy użytkownik będzie mógł zmienić zawartość Variant. Na powrót z wywołania wszelkie zmiany wprowadzone do variant po stronie niezarządzane są propagowane do oryginalnego obiektu. Jeśli typ variant różni się od typu Variant przekazany do wywołania, zmiany są propagowane do obiektu innego typu. Oznacza to, że typ obiektu przekazanego do wywołania może się różnić od typu obiektu zwróconego z wywołania.  
  
-   Podczas przekazywania wariant do kodu zarządzanego przez odwołanie, organizator tworzy nowy obiekt i kopiuje zawartość Variant do obiektu przed wykonaniem połączenia. Odwołanie do obiektu są przekazywane do funkcji zarządzanych, gdy użytkownik będzie mógł zmienić obiektu. Na powrót z wywołania wszelkie zmiany wprowadzone do odwołuje się do obiektu są propagowane do oryginalnego variant. Typ obiektu różni się od typu obiektu przekazany do wywołania, typ wariantu oryginalnego zostanie zmieniona, a wartość jest propagowana do variant. Ponownie typ wariantu przekazany do wywołania mogą się różnić od typu Wariant zwrócona z wywołania.  
  
 **Domyślne zachowanie marshalingu obiektu variant z ustawioną flagą VT_BYREF**  
  
-   Wariant były przekazywane do kodu zarządzanego przez wartość może mieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie zamiast wartości. W takim przypadku wariant jest nadal zorganizować do obiektu, ponieważ wariant jest przekazywany przez wartość. Organizator wyłuskań zawartość wariantu i automatycznie kopiuje go do nowo utworzony obiekt przed wykonaniem połączenia. Obiekt są następnie przekazywane do zarządzanego funkcji; jednak na powrót z wywołania, obiektu nie są propagowane wrócić do oryginalnego variant. Zmiany wprowadzone do zarządzanego obiektu zostaną utracone.  
  
    > [!CAUTION]
    >  Nie istnieje sposób, aby zmienić wartość typu variant przekazany przez wartość, nawet jeśli ma wariant **VT_BYREF** Flaga.  
  
-   Wariant były przekazywane do kodu zarządzanego przez odwołanie może być również **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie do innego. Jeśli tak, wariant jest przekazywane do **ref** obiektu, ponieważ wariant jest przekazywana przez odwołanie. Organizator wyłuskań zawartość wariantu i automatycznie kopiuje go do nowo utworzony obiekt przed wykonaniem połączenia. Na powrót z wywołania wartość obiektu jest propagowana do odwołania w oryginalnej variant tylko wtedy, gdy obiekt jest ten sam typ jak przekazano obiekt. Oznacza to, że propagacja nie zmienia typ wariantu z **VT_BYREF** Flaga. Zmiana typu obiektu podczas wywołania <xref:System.InvalidCastException> występuje na powrót z wywołania.  
  
 W poniższej tabeli przedstawiono reguły propagacji wariantów i obiektów.  
  
|Z|Do|Zmiany propagowane Wstecz|  
|----------|--------|-----------------------------|  
|**Variant***v*|**Obiekt***o*|Nigdy nie|  
|**Obiekt***o*|**Variant***v*|Nigdy nie|  
|**Variant*****\*****pv*|**Odwołanie***o*|Zawsze|  
|**Odwołanie***o*|**Variant*****\*****pv*|Zawsze|  
|**Variant***v* **(VT_BYREF** *&#124;* **VT_\*)**|**Obiekt***o*|Nigdy nie|  
|**Variant***v* **(VT_BYREF** *&#124;* **VT_)**|**Odwołanie***o*|Tylko wtedy, gdy typ nie został zmieniony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)  
 [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)  
 [Atrybuty kierunkową](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))  
 [Kopiowanie i przypinanie](copying-and-pinning.md)
