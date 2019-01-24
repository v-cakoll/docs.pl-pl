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
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="dec85-102">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="dec85-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="dec85-103">Parametry i pola wpisanych w formie <xref:System.Object?displayProperty=nameWithType> mogą łączyć się z kodem niezarządzanym jako jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="dec85-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="dec85-104">Wariant, gdy obiekt jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="dec85-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="dec85-105">Interfejs, gdy obiekt jest polem struktury.</span><span class="sxs-lookup"><span data-stu-id="dec85-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="dec85-106">Tylko Usługa międzyoperacyjna modelu COM obsługuje marshaling dla typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="dec85-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="dec85-107">Zachowanie domyślne jest do organizowania obiektów COM wariantów.</span><span class="sxs-lookup"><span data-stu-id="dec85-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="dec85-108">Te reguły mają zastosowanie tylko do typu **obiektu** i nie mają zastosowania do silnie typizowanych obiektów, które wynikają z **obiektu** klasy.</span><span class="sxs-lookup"><span data-stu-id="dec85-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="dec85-109">Ten temat zawiera następujące informacje dodatkowe na temat marshaling typów obiektów:</span><span class="sxs-lookup"><span data-stu-id="dec85-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="dec85-110">Marshaling opcje</span><span class="sxs-lookup"><span data-stu-id="dec85-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="dec85-111">Kierowanie obiektu na interfejs</span><span class="sxs-lookup"><span data-stu-id="dec85-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="dec85-112">Marshalingu obiektu Variant</span><span class="sxs-lookup"><span data-stu-id="dec85-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="dec85-113">Marshaling wariant do obiektu</span><span class="sxs-lookup"><span data-stu-id="dec85-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="dec85-114">Marshaling wariantów ByRef</span><span class="sxs-lookup"><span data-stu-id="dec85-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="dec85-115">Marshaling opcje</span><span class="sxs-lookup"><span data-stu-id="dec85-115">Marshaling Options</span></span>  
 <span data-ttu-id="dec85-116">W poniższej tabeli przedstawiono opcje kierowania **obiektu** typu danych.</span><span class="sxs-lookup"><span data-stu-id="dec85-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="dec85-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> obiektów marshal wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="dec85-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="dec85-118">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="dec85-118">Enumeration type</span></span>|<span data-ttu-id="dec85-119">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="dec85-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="dec85-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="dec85-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="dec85-121">(ustawienie domyślne dla parametrów)</span><span class="sxs-lookup"><span data-stu-id="dec85-121">(default for parameters)</span></span>|<span data-ttu-id="dec85-122">Wariant styl modelu COM.</span><span class="sxs-lookup"><span data-stu-id="dec85-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="dec85-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="dec85-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="dec85-124">**IDispatch** interfejsu, jeśli jest to możliwe; w przeciwnym razie **IUnknown** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="dec85-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="dec85-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="dec85-126">(ustawienie domyślne dla pól)</span><span class="sxs-lookup"><span data-stu-id="dec85-126">(default for fields)</span></span>|<span data-ttu-id="dec85-127">**IUnknown** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="dec85-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="dec85-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="dec85-129">**IDispatch** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="dec85-130">Poniższy przykład przedstawia definicję interfejsu zarządzanych `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="dec85-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
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
  
 <span data-ttu-id="dec85-131">Poniższy kod eksporty `MarshalObject` interfejsu do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dec85-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
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
>  <span data-ttu-id="dec85-132">Organizator międzyoperacyjny automatycznie zwalnia wszelkie przydzielonego obiektu wewnątrz wariant po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="dec85-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="dec85-133">Poniższy przykład pokazuje typ sformatowanej wartości.</span><span class="sxs-lookup"><span data-stu-id="dec85-133">The following example shows a formatted value type.</span></span>  
  
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
  
 <span data-ttu-id="dec85-134">Poniższy kod umożliwia wyeksportowanie sformatowane typu do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dec85-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="dec85-135">Kierowanie obiektu na interfejs</span><span class="sxs-lookup"><span data-stu-id="dec85-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="dec85-136">Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejs klasy typu zarządzanego <xref:System.Object> ( **_obiekt** interfejsu).</span><span class="sxs-lookup"><span data-stu-id="dec85-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="dec85-137">Ten interfejs jest wpisana jako **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) lub **IUnknown** (**UnmanagedType.IUnknown**) w wynikowej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="dec85-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="dec85-138">Klienci COM dynamicznie wywołać członków klasy zarządzanej lub członków implementowany przez jej klasy pochodne za pośrednictwem **_obiekt** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="dec85-139">Klienta można również wywołać **QueryInterface** do uzyskania innych interfejsu jawnie implementowana przez typ zarządzany.</span><span class="sxs-lookup"><span data-stu-id="dec85-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="dec85-140">Marshalingu obiektu Variant</span><span class="sxs-lookup"><span data-stu-id="dec85-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="dec85-141">Gdy obiekt jest przekazywany do typu variant, wewnętrzny typ wariantu jest określana w czasie wykonywania, na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="dec85-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="dec85-142">Jeśli odwołanie do obiektu ma wartość null (**nic** w języku Visual Basic), obiekt jest przekazywany do wariant typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="dec85-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="dec85-143">Jeśli obiekt jest wystąpieniem typu wymienione w poniższej tabeli, wynikowy typ wariantu zależy od reguł wbudowanych w organizator i wyświetlane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="dec85-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="dec85-144">Inne obiekty, które należy jawnie kontrolować zachowanie marshalingu można zaimplementować <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="dec85-145">W takim przypadku typ wariantu zależy od kodu typ zwracany z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dec85-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dec85-146">W przeciwnym razie, obiekt jest organizowana jako wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="dec85-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="dec85-147">Marshaling System typów Variant</span><span class="sxs-lookup"><span data-stu-id="dec85-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="dec85-148">W poniższej tabeli przedstawiono typy obiektów zarządzanych oraz odpowiadające typy variant COM.</span><span class="sxs-lookup"><span data-stu-id="dec85-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="dec85-149">Te typy są konwertowane tylko wtedy, gdy podpis metody wywołanego typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dec85-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="dec85-150">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="dec85-150">Object type</span></span>|<span data-ttu-id="dec85-151">Typ wariantu COM</span><span class="sxs-lookup"><span data-stu-id="dec85-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="dec85-152">Wartość null, odwołanie do obiektu (**nic** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dec85-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="dec85-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="dec85-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="dec85-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="dec85-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="dec85-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="dec85-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="dec85-156">**VT_ERROR** z **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="dec85-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="dec85-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="dec85-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="dec85-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="dec85-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="dec85-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="dec85-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="dec85-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="dec85-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="dec85-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="dec85-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="dec85-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="dec85-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="dec85-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="dec85-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="dec85-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="dec85-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="dec85-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="dec85-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="dec85-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="dec85-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="dec85-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="dec85-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="dec85-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="dec85-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="dec85-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="dec85-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="dec85-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="dec85-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="dec85-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="dec85-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="dec85-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="dec85-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="dec85-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="dec85-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="dec85-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="dec85-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="dec85-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="dec85-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="dec85-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="dec85-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="dec85-177">Za pomocą `MarshalObject` interfejsem zdefiniowanym w poprzednim przykładzie, w poniższym przykładzie kodu pokazano, jak przekazać różnego rodzaju wariantów do serwera COM.</span><span class="sxs-lookup"><span data-stu-id="dec85-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="dec85-178">Może być organizowany typy modelu COM, które nie mają odpowiednich typów zarządzanych przy użyciu klasy otoki, takich jak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, i <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="dec85-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="dec85-179">Poniższy przykład kodu pokazuje, jak przekazać różnego rodzaju wariantów do serwera COM za pomocą te otoki.</span><span class="sxs-lookup"><span data-stu-id="dec85-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="dec85-180">Klasy otok są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="dec85-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="dec85-181">Organizowanie interfejsu IConvertible Variant</span><span class="sxs-lookup"><span data-stu-id="dec85-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="dec85-182">Typy inne niż te wymienione w poprzedniej sekcji można kontrolować, jak są organizowane przez zaimplementowanie <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="dec85-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="dec85-183">Jeśli obiekt implementuje **IConvertible** interfejs, typ wariantu COM jest ustalany w czasie wykonywania wartość <xref:System.TypeCode> wyliczenie zwróciło <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dec85-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="dec85-184">W poniższej tabeli przedstawiono możliwe wartości **elementu TypeCode** wyliczenie i odpowiedni typ wariantu COM dla każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="dec85-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="dec85-185">TypeCode</span><span class="sxs-lookup"><span data-stu-id="dec85-185">TypeCode</span></span>|<span data-ttu-id="dec85-186">Typ wariantu COM</span><span class="sxs-lookup"><span data-stu-id="dec85-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="dec85-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="dec85-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="dec85-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="dec85-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="dec85-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="dec85-189">**TypeCode.Object**</span></span>|<span data-ttu-id="dec85-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="dec85-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="dec85-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="dec85-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="dec85-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="dec85-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="dec85-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="dec85-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="dec85-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="dec85-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="dec85-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="dec85-195">**TypeCode.Char**</span></span>|<span data-ttu-id="dec85-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="dec85-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="dec85-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="dec85-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="dec85-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="dec85-198">**VT_I1**</span></span>|  
|<span data-ttu-id="dec85-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="dec85-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="dec85-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="dec85-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="dec85-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="dec85-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="dec85-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="dec85-202">**VT_I2**</span></span>|  
|<span data-ttu-id="dec85-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="dec85-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="dec85-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="dec85-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="dec85-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="dec85-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="dec85-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="dec85-206">**VT_I4**</span></span>|  
|<span data-ttu-id="dec85-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="dec85-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="dec85-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="dec85-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="dec85-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="dec85-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="dec85-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="dec85-210">**VT_I8**</span></span>|  
|<span data-ttu-id="dec85-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="dec85-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="dec85-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="dec85-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="dec85-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="dec85-213">**TypeCode.Single**</span></span>|<span data-ttu-id="dec85-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="dec85-214">**VT_R4**</span></span>|  
|<span data-ttu-id="dec85-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="dec85-215">**TypeCode.Double**</span></span>|<span data-ttu-id="dec85-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="dec85-216">**VT_R8**</span></span>|  
|<span data-ttu-id="dec85-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="dec85-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="dec85-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="dec85-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="dec85-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="dec85-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="dec85-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="dec85-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="dec85-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="dec85-221">**TypeCode.String**</span></span>|<span data-ttu-id="dec85-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="dec85-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="dec85-223">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-223">Not supported.</span></span>|<span data-ttu-id="dec85-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="dec85-224">**VT_INT**</span></span>|  
|<span data-ttu-id="dec85-225">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-225">Not supported.</span></span>|<span data-ttu-id="dec85-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="dec85-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="dec85-227">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-227">Not supported.</span></span>|<span data-ttu-id="dec85-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="dec85-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="dec85-229">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-229">Not supported.</span></span>|<span data-ttu-id="dec85-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="dec85-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="dec85-231">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-231">Not supported.</span></span>|<span data-ttu-id="dec85-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="dec85-232">**VT_CY**</span></span>|  
|<span data-ttu-id="dec85-233">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-233">Not supported.</span></span>|<span data-ttu-id="dec85-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="dec85-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="dec85-235">Wartość wariantu COM jest określana przez wywołanie metody **IConvertible.To** *typu* interfejsu, gdzie **do** *typu* jest konwersja Procedura, która odnosi się do typu, który został zwrócony z **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="dec85-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="dec85-236">Na przykład, obiekt, który zwraca **TypeCode.Double** z **IConvertible.GetTypeCode** jest organizowana jako wariant COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="dec85-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="dec85-237">Można uzyskać wartość wariantu (przechowywane w **dblVal** pole wariant COM) przez rzutowanie do **IConvertible** interfejsu i wywoływania <xref:System.IConvertible.ToDouble%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dec85-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="dec85-238">Marshaling wariant do obiektu</span><span class="sxs-lookup"><span data-stu-id="dec85-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="dec85-239">Generowane po marshaling wariant do obiektu, typ i czasami wartość wariantu zorganizowanej Określa typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="dec85-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="dec85-240">W poniższej tabeli przedstawiono każdy typ wariantu i odpowiedni typ obiektu, tworzącą Organizator, gdy wariant jest przekazywany z modelu COM do programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dec85-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="dec85-241">Typ wariantu COM</span><span class="sxs-lookup"><span data-stu-id="dec85-241">COM variant type</span></span>|<span data-ttu-id="dec85-242">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="dec85-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="dec85-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="dec85-243">**VT_EMPTY**</span></span>|<span data-ttu-id="dec85-244">Wartość null, odwołanie do obiektu (**nic** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="dec85-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="dec85-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="dec85-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="dec85-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="dec85-247">**.__ComObject** lub wartość null, jeśli (pdispVal == wartość null)</span><span class="sxs-lookup"><span data-stu-id="dec85-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="dec85-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="dec85-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="dec85-249">**.__ComObject** lub wartość null, jeśli (punkVal == wartość null)</span><span class="sxs-lookup"><span data-stu-id="dec85-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="dec85-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="dec85-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="dec85-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="dec85-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="dec85-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="dec85-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="dec85-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="dec85-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="dec85-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="dec85-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="dec85-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="dec85-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="dec85-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="dec85-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="dec85-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="dec85-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="dec85-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="dec85-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-267">**VT_ARRAY** &AMP;#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="dec85-267">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="dec85-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="dec85-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="dec85-269">**VT_RECORD**</span></span>|<span data-ttu-id="dec85-270">Odpowiadające opakowanym typem wartościowym.</span><span class="sxs-lookup"><span data-stu-id="dec85-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="dec85-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="dec85-271">**VT_VARIANT**</span></span>|<span data-ttu-id="dec85-272">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="dec85-272">Not supported.</span></span>|  
  
 <span data-ttu-id="dec85-273">Typów Variant przekazywane z modelu COM do kodu zarządzanego, a następnie powrót do COM mogą nie zawierać tego samego typu variant na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="dec85-274">Należy wziąć pod uwagę, co się stanie po wariant typu **VT_DISPATCH** jest przekazywany z modelu COM do programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dec85-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="dec85-275">Podczas przekazywania międzyprocesowego, wariant jest konwertowany na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dec85-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dec85-276">Jeśli **obiektu** jest następnie przekazywany do modelu COM, jest przekazywany do wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="dec85-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="dec85-277">Nie ma żadnej gwarancji, że wariant generowana, gdy obiekt jest przekazywany z kodu zarządzanego w modelu COM będzie tego samego typu jako wariant początkowo użyta do wyprodukowania obiektu.</span><span class="sxs-lookup"><span data-stu-id="dec85-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="dec85-278">Marshaling wariantów ByRef</span><span class="sxs-lookup"><span data-stu-id="dec85-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="dec85-279">Mimo że wariantów sami mogą być przekazywane przez wartość lub przez odwołanie, **VT_BYREF** flagi również można używać z dowolnego typu variant do wskazania, że zawartość wariant są przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="dec85-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="dec85-280">Różnica między organizowania wariantów przez odwołanie i organizowanie wariant z **VT_BYREF** ustawioną flagą może być mylące.</span><span class="sxs-lookup"><span data-stu-id="dec85-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="dec85-281">Na poniższej ilustracji wyjaśnia różnice.</span><span class="sxs-lookup"><span data-stu-id="dec85-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="dec85-282">![Wariant przekazywane na stosie](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="dec85-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="dec85-283">Warianty przekazywane według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="dec85-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="dec85-284">**Domyślne zachowanie w przypadku kierowania obiektami i wariantów według wartości**</span><span class="sxs-lookup"><span data-stu-id="dec85-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="dec85-285">Przy przekazywaniu obiektów z kodu zarządzanego w modelu COM, zawartość obiektu są kopiowane do nowy wariant utworzone przez organizatora przy użyciu reguł zdefiniowanych w [Marshalingu obiektu Variant](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="dec85-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="dec85-286">Zmiany wprowadzone do wariantu w niezarządzanym nie są propagowane do oryginalnego obiektu na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="dec85-287">Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariant są kopiowane do nowo utworzonego obiektu przy użyciu reguł zdefiniowanych w [Marshaling wariant obiektowi](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="dec85-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="dec85-288">Zmiany wprowadzone do obiektu zarządzanego stronie nie są propagowane do oryginalnego wariant na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="dec85-289">**Domyślne zachowanie w przypadku kierowania obiektami i wariantów przez odwołanie**</span><span class="sxs-lookup"><span data-stu-id="dec85-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="dec85-290">Propagowanie zmian obiektu wywołującego, parametry muszą być przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="dec85-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="dec85-291">Na przykład, można użyć **ref** — słowo kluczowe w C# (lub **ByRef** kodu zarządzanego w języku Visual Basic) do przekazania parametrów poprzez odniesienie.</span><span class="sxs-lookup"><span data-stu-id="dec85-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="dec85-292">W modelu COM, parametry odwołania są przekazywane za pomocą wskaźnika, takich jak **wariant \*** .</span><span class="sxs-lookup"><span data-stu-id="dec85-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="dec85-293">Podczas przekazywania obiektu dla modelu COM przez odwołanie, organizator tworzy nowy wariant i kopiuje zawartość odwołanie do obiektu do wariant, zanim zostanie nawiązane połączenie.</span><span class="sxs-lookup"><span data-stu-id="dec85-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="dec85-294">Wariant jest przekazywany do niezarządzanej funkcji, w których użytkownik będzie mógł zmienić zawartość wariant.</span><span class="sxs-lookup"><span data-stu-id="dec85-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="dec85-295">Na powrót z wywołania wszelkie zmiany wprowadzone do wariantu w niezarządzanym jest propagowany z powrotem do oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="dec85-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="dec85-296">Jeśli typ variant różni się od typu variant, podawaną do wywołania, zmiany są propagowane do obiektu innego typu.</span><span class="sxs-lookup"><span data-stu-id="dec85-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="dec85-297">Oznacza to, że typ obiektu przekazanego do wywołania mogą się różnić od typu Obiekt zwrócony z wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="dec85-298">Przy przekazywaniu wariant z kodem zarządzanym przez odwołanie, organizator tworzy nowy obiekt i kopiuje zawartość wariant do obiektu, przed wykonaniem wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="dec85-299">Odwołanie do obiektu jest przekazywany do funkcji zarządzanej, gdzie użytkownik jest bezpłatna do zmiany obiektu.</span><span class="sxs-lookup"><span data-stu-id="dec85-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="dec85-300">Na powrót z wywołania wszelkie zmiany wprowadzone do przywoływanego obiektu jest propagowany z powrotem do oryginalnego wariant.</span><span class="sxs-lookup"><span data-stu-id="dec85-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="dec85-301">Jeśli typ obiektu różni się od typu obiektu przekazanego do wywołania, typ wariantu, oryginalnym zostanie zmieniony, a wartość jest propagowany z powrotem do wariant.</span><span class="sxs-lookup"><span data-stu-id="dec85-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="dec85-302">Ponownie typ wariantu przekazane do wywołania mogą się różnić od typu variant, zwrócony z wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="dec85-303">**Domyślne zachowanie marshalingu wariant z ustawioną flagą VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="dec85-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="dec85-304">Wariant został przekazany do kodu zarządzanego przez wartość może mieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołania, a nie wartość.</span><span class="sxs-lookup"><span data-stu-id="dec85-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="dec85-305">W tym przypadku wariant jest nadal zorganizować do obiektu, ponieważ wariant jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="dec85-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="dec85-306">Organizator wyłuskań zawartość wariant i automatycznie kopiuje go do nowo utworzonego obiektu przed wykonaniem wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="dec85-307">Obiekt jest następnie przekazywany do funkcji zarządzanej; jednak na powrót z wywołania, obiekt nie są propagowane do oryginalnego wariant.</span><span class="sxs-lookup"><span data-stu-id="dec85-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="dec85-308">Zmiany wprowadzone do obiektu zarządzanego, zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="dec85-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="dec85-309">Nie ma sposobu na zmianę wartości przekazywane przez wartość wariantu, nawet wtedy, gdy ma wariant **VT_BYREF** Flaga.</span><span class="sxs-lookup"><span data-stu-id="dec85-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="dec85-310">Wariant został przekazany do kodu zarządzanego przez odwołanie mogą też istnieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie do innego.</span><span class="sxs-lookup"><span data-stu-id="dec85-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="dec85-311">Jeśli tak jest, wariant jest przekazywane do **ref** obiektu, ponieważ wariant jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="dec85-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="dec85-312">Organizator wyłuskań zawartość wariant i automatycznie kopiuje go do nowo utworzonego obiektu przed wykonaniem wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="dec85-313">Na powrót z wywołania wartość obiektu jest propagowany z powrotem do odwołania w oryginalnym wariant tylko wtedy, gdy obiekt jest tego samego typu, ponieważ obiekt przekazany w.</span><span class="sxs-lookup"><span data-stu-id="dec85-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="dec85-314">Oznacza to, że propagacja nie zmienia typ zmiennej za pomocą **VT_BYREF** Flaga.</span><span class="sxs-lookup"><span data-stu-id="dec85-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="dec85-315">Typ obiektu po zmianie podczas wywołania, <xref:System.InvalidCastException> występuje na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="dec85-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="dec85-316">W poniższej tabeli przedstawiono zasady propagacji wariantów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="dec85-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="dec85-317">Z</span><span class="sxs-lookup"><span data-stu-id="dec85-317">From</span></span>|<span data-ttu-id="dec85-318">Zadanie</span><span class="sxs-lookup"><span data-stu-id="dec85-318">To</span></span>|<span data-ttu-id="dec85-319">Zmiany propagowany z powrotem</span><span class="sxs-lookup"><span data-stu-id="dec85-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="dec85-320">\**Wariant\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="dec85-320">**Variant**  *v*</span></span>|<span data-ttu-id="dec85-321">\**Obiekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-321">**Object**  *o*</span></span>|<span data-ttu-id="dec85-322">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="dec85-322">Never</span></span>|  
|<span data-ttu-id="dec85-323">\**Obiekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-323">**Object**  *o*</span></span>|<span data-ttu-id="dec85-324">\**Wariant\*\*\*v* </span><span class="sxs-lookup"><span data-stu-id="dec85-324">**Variant**  *v*</span></span>|<span data-ttu-id="dec85-325">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="dec85-325">Never</span></span>|  
|<span data-ttu-id="dec85-326">**Variant**  ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="dec85-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="dec85-327">\**Obiekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="dec85-328">zawsze</span><span class="sxs-lookup"><span data-stu-id="dec85-328">Always</span></span>|  
|<span data-ttu-id="dec85-329">\**Obiekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-329">**Ref object**  *o*</span></span>|<span data-ttu-id="dec85-330">**Variant**  ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="dec85-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="dec85-331">zawsze</span><span class="sxs-lookup"><span data-stu-id="dec85-331">Always</span></span>|  
|<span data-ttu-id="dec85-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="dec85-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="dec85-333">\**Obiekt\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-333">**Object**  *o*</span></span>|<span data-ttu-id="dec85-334">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="dec85-334">Never</span></span>|  
|<span data-ttu-id="dec85-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="dec85-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="dec85-336">\**Obiekt REF\*\*\*o* </span><span class="sxs-lookup"><span data-stu-id="dec85-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="dec85-337">Tylko wtedy, gdy typ nie uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="dec85-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dec85-338">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dec85-338">See also</span></span>
- [<span data-ttu-id="dec85-339">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="dec85-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="dec85-340">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="dec85-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="dec85-341">[Atrybuty kierunkowe](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dec85-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>
- [<span data-ttu-id="dec85-342">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="dec85-342">Copying and Pinning</span></span>](copying-and-pinning.md)
