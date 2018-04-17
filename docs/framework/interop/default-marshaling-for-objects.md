---
title: Organizowanie domyślne dotyczące obiektów
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6980db381322d354cace38709586e50681ae0a7e
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="5adaa-102">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="5adaa-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="5adaa-103">Parametry i pola typu <xref:System.Object?displayProperty=nameWithType> można wyświetlać do kodu niezarządzanego jako jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="5adaa-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
-   <span data-ttu-id="5adaa-104">Wariant, gdy obiekt jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="5adaa-104">A variant when the object is a parameter.</span></span>  
  
-   <span data-ttu-id="5adaa-105">Interfejs, gdy obiekt jest polem struktury.</span><span class="sxs-lookup"><span data-stu-id="5adaa-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="5adaa-106">Tylko Usługa międzyoperacyjna modelu COM obsługuje przekazywanie dla typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="5adaa-107">Domyślnym zachowaniem jest do organizowania obiektów COM Variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="5adaa-108">Te reguły dotyczą tylko w typie **obiektu** i nie stosuje się do silnie typizowanych obiektów, które pochodzą z **obiektu** klasy.</span><span class="sxs-lookup"><span data-stu-id="5adaa-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
 <span data-ttu-id="5adaa-109">Ten temat zawiera następujące informacje dodatkowe o przekazywanie typów obiektów:</span><span class="sxs-lookup"><span data-stu-id="5adaa-109">This topic provides the following additional information about marshaling object types:</span></span>  
  
-   [<span data-ttu-id="5adaa-110">Organizowanie opcje</span><span class="sxs-lookup"><span data-stu-id="5adaa-110">Marshaling Options</span></span>](#cpcondefaultmarshalingforobjectsanchor7)  
  
-   [<span data-ttu-id="5adaa-111">Przekazywanie obiektu na interfejs</span><span class="sxs-lookup"><span data-stu-id="5adaa-111">Marshaling Object to Interface</span></span>](#cpcondefaultmarshalingforobjectsanchor2)  
  
-   [<span data-ttu-id="5adaa-112">Kierowanie obiektu do typu Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-112">Marshaling Object to Variant</span></span>](#cpcondefaultmarshalingforobjectsanchor3)  
  
-   [<span data-ttu-id="5adaa-113">Organizowanie Variant do obiektu</span><span class="sxs-lookup"><span data-stu-id="5adaa-113">Marshaling Variant to Object</span></span>](#cpcondefaultmarshalingforobjectsanchor4)  
  
-   [<span data-ttu-id="5adaa-114">Organizowanie ByRef Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-114">Marshaling ByRef Variants</span></span>](#cpcondefaultmarshalingforobjectsanchor6)  
  
<a name="cpcondefaultmarshalingforobjectsanchor7"></a>   
## <a name="marshaling-options"></a><span data-ttu-id="5adaa-115">Organizowanie opcje</span><span class="sxs-lookup"><span data-stu-id="5adaa-115">Marshaling Options</span></span>  
 <span data-ttu-id="5adaa-116">W poniższej tabeli przedstawiono opcje organizowania **obiektu** — typ danych.</span><span class="sxs-lookup"><span data-stu-id="5adaa-116">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="5adaa-117"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-117">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="5adaa-118">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5adaa-118">Enumeration type</span></span>|<span data-ttu-id="5adaa-119">Opis formatu niezarządzane</span><span class="sxs-lookup"><span data-stu-id="5adaa-119">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="5adaa-120">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="5adaa-120">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="5adaa-121">(ustawienie domyślne dla parametrów)</span><span class="sxs-lookup"><span data-stu-id="5adaa-121">(default for parameters)</span></span>|<span data-ttu-id="5adaa-122">Styl modelu COM variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-122">A COM-style variant.</span></span>|  
|<span data-ttu-id="5adaa-123">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="5adaa-123">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="5adaa-124">**IDispatch** interfejsu, jeśli to możliwe, a w przeciwnym razie **IUnknown** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-124">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="5adaa-125">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="5adaa-125">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="5adaa-126">(domyślnie dla pola)</span><span class="sxs-lookup"><span data-stu-id="5adaa-126">(default for fields)</span></span>|<span data-ttu-id="5adaa-127">**IUnknown** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-127">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="5adaa-128">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="5adaa-128">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="5adaa-129">**IDispatch** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-129">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="5adaa-130">W poniższym przykładzie przedstawiono definicję interfejsu zarządzanego `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="5adaa-130">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
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
  
 <span data-ttu-id="5adaa-131">Poniższy kod eksportuje `MarshalObject` interfejs do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-131">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
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
>  <span data-ttu-id="5adaa-132">Organizator międzyoperacyjnego automatycznie zwalnia dowolnego przydzielonego obiektu wewnątrz wariant po wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="5adaa-132">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="5adaa-133">W poniższym przykładzie przedstawiono typu sformatowana wartość.</span><span class="sxs-lookup"><span data-stu-id="5adaa-133">The following example shows a formatted value type.</span></span>  
  
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
  
 <span data-ttu-id="5adaa-134">Poniższy kod eksportuje sformatowany typu do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-134">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
<a name="cpcondefaultmarshalingforobjectsanchor2"></a>   
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="5adaa-135">Przekazywanie obiektu na interfejs</span><span class="sxs-lookup"><span data-stu-id="5adaa-135">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="5adaa-136">Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejs klasy dla typu zarządzanego <xref:System.Object> ( **_Object** interfejs).</span><span class="sxs-lookup"><span data-stu-id="5adaa-136">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="5adaa-137">Ten interfejs jest typu **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) lub **IUnknown** (**UnmanagedType.IUnknown**) w wynikowej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-137">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="5adaa-138">Klientów modelu COM. można dynamicznie wywołać członkami zarządzanej klasy lub członków implementowane przez jej klas pochodnych za pośrednictwem **_Object** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-138">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="5adaa-139">Klient może także wywołać **QueryInterface** uzyskać inny interfejs jawnie implementowana przez typ zarządzany.</span><span class="sxs-lookup"><span data-stu-id="5adaa-139">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor3"></a>   
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="5adaa-140">Kierowanie obiektu do typu Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-140">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="5adaa-141">Gdy obiekt jest przekazywane do typu variant, wewnętrzny typ wariantu jest określany w czasie wykonywania na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="5adaa-141">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
-   <span data-ttu-id="5adaa-142">Jeśli odwołanie do obiektu ma wartość null (**nic** w języku Visual Basic), obiekt jest przekazywane do wariant typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="5adaa-142">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
-   <span data-ttu-id="5adaa-143">Jeśli obiekt jest wystąpieniem typu wymienione w poniższej tabeli, wynikowy typ wariantu zależy od reguł wbudowanych w organizatora i wyświetlany w tabeli.</span><span class="sxs-lookup"><span data-stu-id="5adaa-143">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
-   <span data-ttu-id="5adaa-144">Inne obiekty, które trzeba jawnie kontrolować zachowanie marshalingu można zaimplementować <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-144">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="5adaa-145">W takim przypadku typ wariantu jest określany przez kod typ zwrócony z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5adaa-145">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5adaa-146">W przeciwnym razie wartość obiektu jest przekazywane jako wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="5adaa-146">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="5adaa-147">Organizowanie System typów Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-147">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="5adaa-148">W poniższej tabeli przedstawiono typy zarządzanych obiektów i odpowiednie typy variant modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5adaa-148">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="5adaa-149">Te typy są konwertowane tylko wtedy, gdy podpis metody wywoływanej jest typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5adaa-149">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="5adaa-150">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="5adaa-150">Object type</span></span>|<span data-ttu-id="5adaa-151">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="5adaa-151">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="5adaa-152">Odwołanie do obiektu o wartości null (**nic** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5adaa-152">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="5adaa-153">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-153">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="5adaa-154">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-154">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="5adaa-155">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="5adaa-155">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="5adaa-156">**VT_ERROR** z **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="5adaa-156">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="5adaa-157">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="5adaa-157">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="5adaa-158">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="5adaa-158">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="5adaa-159">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-159">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="5adaa-160">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-160">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="5adaa-161">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-161">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="5adaa-162">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-162">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="5adaa-163">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-163">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="5adaa-164">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-164">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="5adaa-165">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-165">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="5adaa-166">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-166">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="5adaa-167">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-167">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="5adaa-168">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-168">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="5adaa-169">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-169">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="5adaa-170">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-170">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="5adaa-171">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-171">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="5adaa-172">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="5adaa-172">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="5adaa-173">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="5adaa-173">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="5adaa-174">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-174">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="5adaa-175">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-175">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="5adaa-176">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-176">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="5adaa-177">Przy użyciu `MarshalObject` interfejs zdefiniowany w poprzednim przykładzie, w poniższym przykładzie pokazano, jak do przekazania na serwer COM różnego typu Variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-177">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="5adaa-178">Typy modelu COM, które nie mają odpowiednie typy zarządzane być organizowany przy użyciu klasy otoki, takich jak <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, i <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="5adaa-178">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="5adaa-179">Poniższy przykład kodu pokazuje, jak na potrzeby przekazania różnego typu Variant do serwera COM. te otoki.</span><span class="sxs-lookup"><span data-stu-id="5adaa-179">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="5adaa-180">Klasy otok są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5adaa-180">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="5adaa-181">Organizowanie interfejs IConvertible Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-181">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="5adaa-182">Typów innych niż wymienione w poprzedniej sekcji można kontrolować, jak są przekazywane przez zaimplementowanie <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-182">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="5adaa-183">Jeśli obiekt implementuje **IConvertible** interfejsu typu variant modelu COM jest określana w czasie wykonywania przez wartość <xref:System.TypeCode> wyliczenie zwrócony z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5adaa-183">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5adaa-184">W poniższej tabeli przedstawiono możliwe wartości **elementu TypeCode** wyliczenie i odpowiedniego typu variant modelu COM dla każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="5adaa-184">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="5adaa-185">TypeCode</span><span class="sxs-lookup"><span data-stu-id="5adaa-185">TypeCode</span></span>|<span data-ttu-id="5adaa-186">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="5adaa-186">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="5adaa-187">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="5adaa-187">**TypeCode.Empty**</span></span>|<span data-ttu-id="5adaa-188">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-188">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="5adaa-189">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="5adaa-189">**TypeCode.Object**</span></span>|<span data-ttu-id="5adaa-190">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="5adaa-190">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="5adaa-191">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="5adaa-191">**TypeCode.DBNull**</span></span>|<span data-ttu-id="5adaa-192">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-192">**VT_NULL**</span></span>|  
|<span data-ttu-id="5adaa-193">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="5adaa-193">**TypeCode.Boolean**</span></span>|<span data-ttu-id="5adaa-194">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-194">**VT_BOOL**</span></span>|  
|<span data-ttu-id="5adaa-195">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="5adaa-195">**TypeCode.Char**</span></span>|<span data-ttu-id="5adaa-196">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-196">**VT_UI2**</span></span>|  
|<span data-ttu-id="5adaa-197">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="5adaa-197">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="5adaa-198">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-198">**VT_I1**</span></span>|  
|<span data-ttu-id="5adaa-199">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="5adaa-199">**TypeCode.Byte**</span></span>|<span data-ttu-id="5adaa-200">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-200">**VT_UI1**</span></span>|  
|<span data-ttu-id="5adaa-201">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="5adaa-201">**TypeCode.Int16**</span></span>|<span data-ttu-id="5adaa-202">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-202">**VT_I2**</span></span>|  
|<span data-ttu-id="5adaa-203">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="5adaa-203">**TypeCode.UInt16**</span></span>|<span data-ttu-id="5adaa-204">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-204">**VT_UI2**</span></span>|  
|<span data-ttu-id="5adaa-205">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="5adaa-205">**TypeCode.Int32**</span></span>|<span data-ttu-id="5adaa-206">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-206">**VT_I4**</span></span>|  
|<span data-ttu-id="5adaa-207">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="5adaa-207">**TypeCode.UInt32**</span></span>|<span data-ttu-id="5adaa-208">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-208">**VT_UI4**</span></span>|  
|<span data-ttu-id="5adaa-209">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="5adaa-209">**TypeCode.Int64**</span></span>|<span data-ttu-id="5adaa-210">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-210">**VT_I8**</span></span>|  
|<span data-ttu-id="5adaa-211">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="5adaa-211">**TypeCode.UInt64**</span></span>|<span data-ttu-id="5adaa-212">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-212">**VT_UI8**</span></span>|  
|<span data-ttu-id="5adaa-213">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="5adaa-213">**TypeCode.Single**</span></span>|<span data-ttu-id="5adaa-214">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-214">**VT_R4**</span></span>|  
|<span data-ttu-id="5adaa-215">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="5adaa-215">**TypeCode.Double**</span></span>|<span data-ttu-id="5adaa-216">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-216">**VT_R8**</span></span>|  
|<span data-ttu-id="5adaa-217">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="5adaa-217">**TypeCode.Decimal**</span></span>|<span data-ttu-id="5adaa-218">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-218">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="5adaa-219">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="5adaa-219">**TypeCode.DateTime**</span></span>|<span data-ttu-id="5adaa-220">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="5adaa-220">**VT_DATE**</span></span>|  
|<span data-ttu-id="5adaa-221">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="5adaa-221">**TypeCode.String**</span></span>|<span data-ttu-id="5adaa-222">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="5adaa-222">**VT_BSTR**</span></span>|  
|<span data-ttu-id="5adaa-223">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-223">Not supported.</span></span>|<span data-ttu-id="5adaa-224">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-224">**VT_INT**</span></span>|  
|<span data-ttu-id="5adaa-225">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-225">Not supported.</span></span>|<span data-ttu-id="5adaa-226">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-226">**VT_UINT**</span></span>|  
|<span data-ttu-id="5adaa-227">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-227">Not supported.</span></span>|<span data-ttu-id="5adaa-228">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-228">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="5adaa-229">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-229">Not supported.</span></span>|<span data-ttu-id="5adaa-230">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="5adaa-230">**VT_RECORD**</span></span>|  
|<span data-ttu-id="5adaa-231">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-231">Not supported.</span></span>|<span data-ttu-id="5adaa-232">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-232">**VT_CY**</span></span>|  
|<span data-ttu-id="5adaa-233">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-233">Not supported.</span></span>|<span data-ttu-id="5adaa-234">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-234">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="5adaa-235">Wartość variant modelu COM jest określana przez wywołanie metody **IConvertible.To** *typu* interfejsu, gdzie **do** *typu* jest konwersji Procedura umożliwiająca typ, który został zwrócony z **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="5adaa-235">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="5adaa-236">Na przykład obiekt, który zwraca **TypeCode.Double** z **IConvertible.GetTypeCode** jest przekazywane jako typ variant modelu COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="5adaa-236">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="5adaa-237">Można uzyskać wartości z wariantu (przechowywane w **dblVal** pole Typ COM variant) przez rzutowanie do **IConvertible** interfejsu i wywoływania <xref:System.IConvertible.ToDouble%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="5adaa-237">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor4"></a>   
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="5adaa-238">Organizowanie Variant do obiektu</span><span class="sxs-lookup"><span data-stu-id="5adaa-238">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="5adaa-239">Gdy organizowanie variant do obiektu, typ i czasami wartość organizowane variant Określa typ obiektu utworzone.</span><span class="sxs-lookup"><span data-stu-id="5adaa-239">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="5adaa-240">W poniższej tabeli przedstawiono każdego typu variant i odpowiedni typ obiektu organizatora tworzy podczas wariant jest przekazywany z modelu COM programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5adaa-240">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="5adaa-241">Typ variant modelu COM</span><span class="sxs-lookup"><span data-stu-id="5adaa-241">COM variant type</span></span>|<span data-ttu-id="5adaa-242">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="5adaa-242">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="5adaa-243">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-243">**VT_EMPTY**</span></span>|<span data-ttu-id="5adaa-244">Odwołanie do obiektu o wartości null (**nic** w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="5adaa-244">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="5adaa-245">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-245">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-246">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="5adaa-246">**VT_DISPATCH**</span></span>|<span data-ttu-id="5adaa-247">**System.__ComObject** lub wartość null, jeśli (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="5adaa-247">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="5adaa-248">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="5adaa-248">**VT_UNKNOWN**</span></span>|<span data-ttu-id="5adaa-249">**System.__ComObject** lub wartość null, jeśli (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="5adaa-249">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="5adaa-250">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="5adaa-250">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-251">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-251">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-252">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-252">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-253">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="5adaa-253">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-254">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-254">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-255">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="5adaa-255">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-256">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-256">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-257">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-257">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-258">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-258">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-259">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-259">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-260">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="5adaa-260">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-261">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="5adaa-261">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-262">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="5adaa-262">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-263">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="5adaa-263">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-264">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="5adaa-264">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-265">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-265">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-266">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-266">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-267">**VT_ARRAY** &AMP;#124; **VT_\***</span><span class="sxs-lookup"><span data-stu-id="5adaa-267">**VT_ARRAY** &#124; **VT_\***</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-268">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="5adaa-268">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="5adaa-269">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="5adaa-269">**VT_RECORD**</span></span>|<span data-ttu-id="5adaa-270">Odpowiadającego opakowanym typem wartościowym.</span><span class="sxs-lookup"><span data-stu-id="5adaa-270">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="5adaa-271">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="5adaa-271">**VT_VARIANT**</span></span>|<span data-ttu-id="5adaa-272">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5adaa-272">Not supported.</span></span>|  
  
 <span data-ttu-id="5adaa-273">Typy Variant przekazany z modelu COM do kodu zarządzanego i następnie powrót do modelu COM mogą nie zawierać ten sam typ variant na czas trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-273">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="5adaa-274">Należy rozważyć, co się stanie po wariant typu **VT_DISPATCH** jest przekazywany z modelu COM programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5adaa-274">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="5adaa-275">Podczas przekazywania międzyprocesowego, wariant jest konwertowana na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5adaa-275">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5adaa-276">Jeśli **obiektu** są następnie przekazywane do modelu COM, jest przekazywane do wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="5adaa-276">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="5adaa-277">Nie ma żadnej gwarancji, że wariant tworzone, gdy obiekt jest przekazywane z kodu zarządzanego w modelu COM będzie taki sam typ jak variant początkowo używane do tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-277">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
<a name="cpcondefaultmarshalingforobjectsanchor6"></a>   
## <a name="marshaling-byref-variants"></a><span data-ttu-id="5adaa-278">Organizowanie ByRef Variant</span><span class="sxs-lookup"><span data-stu-id="5adaa-278">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="5adaa-279">Mimo że wariantów same mogą być przekazywane przez wartości lub według odwołania, **VT_BYREF** flagi można również w przypadku każdego typu variant wskazują, że zawartość wariantu są przekazywany przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="5adaa-279">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="5adaa-280">Różnica między przekazywanie wariantów przez odwołanie i organizowanie wariant z **VT_BYREF** ustawiona flaga może być mylące.</span><span class="sxs-lookup"><span data-stu-id="5adaa-280">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="5adaa-281">Poniższa ilustracja wyjaśnia różnice.</span><span class="sxs-lookup"><span data-stu-id="5adaa-281">The following illustration clarifies the differences.</span></span>  
  
 <span data-ttu-id="5adaa-282">![Wariant przekazany na stosie](./media/interopvariant.gif "interopvariant")</span><span class="sxs-lookup"><span data-stu-id="5adaa-282">![Variant passed on the stack](./media/interopvariant.gif "interopvariant")</span></span>  
<span data-ttu-id="5adaa-283">Wariantów przekazywane według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="5adaa-283">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="5adaa-284">**Domyślne zachowanie dla organizowanie obiektów i wariantów przez wartość**</span><span class="sxs-lookup"><span data-stu-id="5adaa-284">**Default behavior for marshaling objects and variants by value**</span></span>  
  
-   <span data-ttu-id="5adaa-285">Podczas przekazywania obiektów z kodu zarządzanego w modelu COM, zawartość obiektu są kopiowane do nowego wariant utworzone przez organizatora, za pomocą reguł zdefiniowanych w [kierowanie obiektu Variant](#cpcondefaultmarshalingforobjectsanchor3).</span><span class="sxs-lookup"><span data-stu-id="5adaa-285">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#cpcondefaultmarshalingforobjectsanchor3).</span></span> <span data-ttu-id="5adaa-286">Zmiany wprowadzone do wariantu po stronie niezarządzane nie są propagowane do oryginalnego obiektu na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-286">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
-   <span data-ttu-id="5adaa-287">Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariantu są kopiowane do nowo utworzony obiekt, za pomocą reguł zdefiniowanych w [Variant przekazywanie do obiektu](#cpcondefaultmarshalingforobjectsanchor4).</span><span class="sxs-lookup"><span data-stu-id="5adaa-287">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#cpcondefaultmarshalingforobjectsanchor4).</span></span> <span data-ttu-id="5adaa-288">Zmiany wprowadzone do obiektu po stronie zarządzanego nie są propagowane do oryginalnego variant na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-288">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="5adaa-289">**Domyślne zachowanie dla organizowanie obiektów i wariantów przez odwołanie**</span><span class="sxs-lookup"><span data-stu-id="5adaa-289">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="5adaa-290">Propagowanie zmian z powrotem na obiekt wywołujący, parametry muszą być przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5adaa-290">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="5adaa-291">Na przykład można użyć **ref** — słowo kluczowe języka C# (lub **ByRef** kodu zarządzanego w języku Visual Basic) do przekazania parametrów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5adaa-291">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="5adaa-292">W modelu COM, odwołanie parametry są przekazywane, takich jak przy użyciu wskaźnika **variant \*** .</span><span class="sxs-lookup"><span data-stu-id="5adaa-292">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
-   <span data-ttu-id="5adaa-293">Podczas przekazywania obiektu w modelu COM przez odwołanie, organizatora tworzy nowy typ variant i kopiuje zawartość odwołanie obiektu do variant, przed dokonaniem wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-293">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="5adaa-294">Wariant jest przekazywany do funkcji niezarządzanej, gdy użytkownik będzie mógł zmienić zawartość Variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-294">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="5adaa-295">Na powrót z wywołania wszelkie zmiany wprowadzone do variant po stronie niezarządzane są propagowane do oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-295">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="5adaa-296">Jeśli typ variant różni się od typu Variant przekazany do wywołania, zmiany są propagowane do obiektu innego typu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-296">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="5adaa-297">Oznacza to, że typ obiektu przekazanego do wywołania może się różnić od typu obiektu zwróconego z wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-297">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
-   <span data-ttu-id="5adaa-298">Podczas przekazywania wariant do kodu zarządzanego przez odwołanie, organizator tworzy nowy obiekt i kopiuje zawartość Variant do obiektu przed wykonaniem połączenia.</span><span class="sxs-lookup"><span data-stu-id="5adaa-298">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="5adaa-299">Odwołanie do obiektu są przekazywane do funkcji zarządzanych, gdy użytkownik będzie mógł zmienić obiektu.</span><span class="sxs-lookup"><span data-stu-id="5adaa-299">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="5adaa-300">Na powrót z wywołania wszelkie zmiany wprowadzone do odwołuje się do obiektu są propagowane do oryginalnego variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-300">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="5adaa-301">Typ obiektu różni się od typu obiektu przekazany do wywołania, typ wariantu oryginalnego zostanie zmieniona, a wartość jest propagowana do variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-301">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="5adaa-302">Ponownie typ wariantu przekazany do wywołania mogą się różnić od typu Wariant zwrócona z wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-302">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="5adaa-303">**Domyślne zachowanie marshalingu obiektu variant z ustawioną flagą VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="5adaa-303">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
-   <span data-ttu-id="5adaa-304">Wariant były przekazywane do kodu zarządzanego przez wartość może mieć **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie zamiast wartości.</span><span class="sxs-lookup"><span data-stu-id="5adaa-304">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="5adaa-305">W takim przypadku wariant jest nadal zorganizować do obiektu, ponieważ wariant jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="5adaa-305">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="5adaa-306">Organizator wyłuskań zawartość wariantu i automatycznie kopiuje go do nowo utworzony obiekt przed wykonaniem połączenia.</span><span class="sxs-lookup"><span data-stu-id="5adaa-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="5adaa-307">Obiekt są następnie przekazywane do zarządzanego funkcji; jednak na powrót z wywołania, obiektu nie są propagowane wrócić do oryginalnego variant.</span><span class="sxs-lookup"><span data-stu-id="5adaa-307">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="5adaa-308">Zmiany wprowadzone do zarządzanego obiektu zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="5adaa-308">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="5adaa-309">Nie istnieje sposób, aby zmienić wartość typu variant przekazany przez wartość, nawet jeśli ma wariant **VT_BYREF** Flaga.</span><span class="sxs-lookup"><span data-stu-id="5adaa-309">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
-   <span data-ttu-id="5adaa-310">Wariant były przekazywane do kodu zarządzanego przez odwołanie może być również **VT_BYREF** flaga wskazuje, że wariant zawiera odwołanie do innego.</span><span class="sxs-lookup"><span data-stu-id="5adaa-310">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="5adaa-311">Jeśli tak, wariant jest przekazywane do **ref** obiektu, ponieważ wariant jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="5adaa-311">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="5adaa-312">Organizator wyłuskań zawartość wariantu i automatycznie kopiuje go do nowo utworzony obiekt przed wykonaniem połączenia.</span><span class="sxs-lookup"><span data-stu-id="5adaa-312">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="5adaa-313">Na powrót z wywołania wartość obiektu jest propagowana do odwołania w oryginalnej variant tylko wtedy, gdy obiekt jest ten sam typ jak przekazano obiekt.</span><span class="sxs-lookup"><span data-stu-id="5adaa-313">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="5adaa-314">Oznacza to, że propagacja nie zmienia typ wariantu z **VT_BYREF** Flaga.</span><span class="sxs-lookup"><span data-stu-id="5adaa-314">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="5adaa-315">Zmiana typu obiektu podczas wywołania <xref:System.InvalidCastException> występuje na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="5adaa-315">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="5adaa-316">W poniższej tabeli przedstawiono reguły propagacji wariantów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="5adaa-316">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="5adaa-317">Z</span><span class="sxs-lookup"><span data-stu-id="5adaa-317">From</span></span>|<span data-ttu-id="5adaa-318">Do</span><span class="sxs-lookup"><span data-stu-id="5adaa-318">To</span></span>|<span data-ttu-id="5adaa-319">Zmiany propagowane Wstecz</span><span class="sxs-lookup"><span data-stu-id="5adaa-319">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="5adaa-320">**Variant***v*</span><span class="sxs-lookup"><span data-stu-id="5adaa-320">**Variant**  *v*</span></span>|<span data-ttu-id="5adaa-321">**Obiekt***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-321">**Object**  *o*</span></span>|<span data-ttu-id="5adaa-322">Nigdy nie</span><span class="sxs-lookup"><span data-stu-id="5adaa-322">Never</span></span>|  
|<span data-ttu-id="5adaa-323">**Obiekt***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-323">**Object**  *o*</span></span>|<span data-ttu-id="5adaa-324">**Variant***v*</span><span class="sxs-lookup"><span data-stu-id="5adaa-324">**Variant**  *v*</span></span>|<span data-ttu-id="5adaa-325">Nigdy nie</span><span class="sxs-lookup"><span data-stu-id="5adaa-325">Never</span></span>|  
|<span data-ttu-id="5adaa-326">\**Variant\*\*\*\*\*\*\*\*\*\*pv*</span><span class="sxs-lookup"><span data-stu-id="5adaa-326">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="5adaa-327">**Odwołanie***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-327">**Ref Object**  *o*</span></span>|<span data-ttu-id="5adaa-328">Zawsze</span><span class="sxs-lookup"><span data-stu-id="5adaa-328">Always</span></span>|  
|<span data-ttu-id="5adaa-329">**Odwołanie***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-329">**Ref object**  *o*</span></span>|<span data-ttu-id="5adaa-330">\**Variant\*\*\*\*\*\*\*\*\*\*pv*</span><span class="sxs-lookup"><span data-stu-id="5adaa-330">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="5adaa-331">Zawsze</span><span class="sxs-lookup"><span data-stu-id="5adaa-331">Always</span></span>|  
|<span data-ttu-id="5adaa-332">\**Variant\*\*\*v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="5adaa-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="5adaa-333">**Obiekt***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-333">**Object**  *o*</span></span>|<span data-ttu-id="5adaa-334">Nigdy nie</span><span class="sxs-lookup"><span data-stu-id="5adaa-334">Never</span></span>|  
|<span data-ttu-id="5adaa-335">**Variant***v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="5adaa-335">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="5adaa-336">**Odwołanie***o*</span><span class="sxs-lookup"><span data-stu-id="5adaa-336">**Ref Object**  *o*</span></span>|<span data-ttu-id="5adaa-337">Tylko wtedy, gdy typ nie został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5adaa-337">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5adaa-338">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5adaa-338">See Also</span></span>  
 [<span data-ttu-id="5adaa-339">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="5adaa-339">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="5adaa-340">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="5adaa-340">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="5adaa-341">[Atrybuty kierunkową](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5adaa-341">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="5adaa-342">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="5adaa-342">Copying and Pinning</span></span>](copying-and-pinning.md)
