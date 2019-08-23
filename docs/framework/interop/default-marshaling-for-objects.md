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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bc165c6f1a7cdc6b8a03db0b7648583d75cd7a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946664"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="a5875-102">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="a5875-102">Default Marshaling for Objects</span></span>
<span data-ttu-id="a5875-103">Parametry i pola, które <xref:System.Object?displayProperty=nameWithType> zostały wpisane jako mogą być ujawnione w kodzie niezarządzanym jako jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="a5875-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>  
  
- <span data-ttu-id="a5875-104">Wariant, gdy obiekt jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="a5875-104">A variant when the object is a parameter.</span></span>  
  
- <span data-ttu-id="a5875-105">Interfejs, gdy obiekt jest polem struktury.</span><span class="sxs-lookup"><span data-stu-id="a5875-105">An interface when the object is a structure field.</span></span>  
  
 <span data-ttu-id="a5875-106">Tylko usługa międzyoperacyjna modelu COM obsługuje kierowanie dla typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="a5875-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="a5875-107">Domyślnym zachowaniem jest kierowanie obiektów do wariantów COM.</span><span class="sxs-lookup"><span data-stu-id="a5875-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="a5875-108">Te reguły mają zastosowanie tylko do **obiektu** typu i nie mają zastosowania do obiektów silnie wpisanych, które pochodzą z klasy **Object** .</span><span class="sxs-lookup"><span data-stu-id="a5875-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>  
  
## <a name="marshaling-options"></a><span data-ttu-id="a5875-109">Opcje organizowania</span><span class="sxs-lookup"><span data-stu-id="a5875-109">Marshaling Options</span></span>  
 <span data-ttu-id="a5875-110">W poniższej tabeli przedstawiono opcje organizowania dla typu danych **obiekt** .</span><span class="sxs-lookup"><span data-stu-id="a5875-110">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="a5875-111">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="a5875-111">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>  
  
|<span data-ttu-id="a5875-112">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a5875-112">Enumeration type</span></span>|<span data-ttu-id="a5875-113">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="a5875-113">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="a5875-114">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="a5875-114">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="a5875-115">(domyślnie dla parametrów)</span><span class="sxs-lookup"><span data-stu-id="a5875-115">(default for parameters)</span></span>|<span data-ttu-id="a5875-116">Wariant w stylu COM.</span><span class="sxs-lookup"><span data-stu-id="a5875-116">A COM-style variant.</span></span>|  
|<span data-ttu-id="a5875-117">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="a5875-117">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="a5875-118">Interfejs **IDispatch** , o ile to możliwe; w przeciwnym razie interfejs **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="a5875-118">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|  
|<span data-ttu-id="a5875-119">**UnmanagedType. IUnknown**</span><span class="sxs-lookup"><span data-stu-id="a5875-119">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="a5875-120">(domyślnie dla pól)</span><span class="sxs-lookup"><span data-stu-id="a5875-120">(default for fields)</span></span>|<span data-ttu-id="a5875-121">Interfejs **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="a5875-121">An **IUnknown** interface.</span></span>|  
|<span data-ttu-id="a5875-122">**UnmanagedType. IDispatch**</span><span class="sxs-lookup"><span data-stu-id="a5875-122">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="a5875-123">Interfejs **IDispatch** .</span><span class="sxs-lookup"><span data-stu-id="a5875-123">An **IDispatch** interface.</span></span>|  
  
 <span data-ttu-id="a5875-124">W poniższym przykładzie przedstawiono definicję interfejsu zarządzanego dla programu `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="a5875-124">The following example shows the managed interface definition for `MarshalObject`.</span></span>  
  
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
  
 <span data-ttu-id="a5875-125">Poniższy kod eksportuje `MarshalObject` interfejs do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a5875-125">The following code exports the `MarshalObject` interface to a type library.</span></span>  
  
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
> <span data-ttu-id="a5875-126">Organizator międzyoperacyjny automatycznie zwalnia wszelki przydzielony obiekt wewnątrz wariantu po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="a5875-126">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>  
  
 <span data-ttu-id="a5875-127">Poniższy przykład przedstawia sformatowany typ wartości.</span><span class="sxs-lookup"><span data-stu-id="a5875-127">The following example shows a formatted value type.</span></span>  
  
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
  
 <span data-ttu-id="a5875-128">Poniższy kod eksportuje sformatowany typ do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a5875-128">The following code exports the formatted type to a type library.</span></span>  
  
```  
struct ObjectHolder {  
   VARIANT o1;  
   IDispatch *o2;  
}  
```  
  
## <a name="marshaling-object-to-interface"></a><span data-ttu-id="a5875-129">Kierowanie obiektu do interfejsu</span><span class="sxs-lookup"><span data-stu-id="a5875-129">Marshaling Object to Interface</span></span>  
 <span data-ttu-id="a5875-130">Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejsem klasy dla zarządzanego typu <xref:System.Object> (interfejs **_object** ).</span><span class="sxs-lookup"><span data-stu-id="a5875-130">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="a5875-131">Ten interfejs jest wpisywany jako **IDispatch** <xref:System.Runtime.InteropServices.UnmanagedType>() lub **IUnknown** (UnmanagedType **. IUnknown**) w bibliotece typów będących wynikiem.</span><span class="sxs-lookup"><span data-stu-id="a5875-131">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="a5875-132">Klienci modelu COM mogą dynamicznie wywoływać elementy członkowskie zarządzanej klasy lub wszelkich członków wdrożonych przez klasy pochodne za pomocą interfejsu **_object** .</span><span class="sxs-lookup"><span data-stu-id="a5875-132">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="a5875-133">Klient może również wywołać metodę **QueryInterface** , aby uzyskać inny interfejs jawnie zaimplementowany przez typ zarządzany.</span><span class="sxs-lookup"><span data-stu-id="a5875-133">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>  
  
## <a name="marshaling-object-to-variant"></a><span data-ttu-id="a5875-134">Kierowanie obiektu do wariantu</span><span class="sxs-lookup"><span data-stu-id="a5875-134">Marshaling Object to Variant</span></span>  
 <span data-ttu-id="a5875-135">Gdy obiekt jest zorganizowany do wariantu, wewnętrzny typ Variant jest określany w czasie wykonywania na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="a5875-135">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>  
  
- <span data-ttu-id="a5875-136">Jeśli odwołanie do obiektu ma wartość null (**Nothing** w Visual Basic), obiekt jest zorganizowany do wariantu typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="a5875-136">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>  
  
- <span data-ttu-id="a5875-137">Jeśli obiekt jest wystąpieniem dowolnego typu wymienionych w poniższej tabeli, wynikowy typ Variant jest określany przez reguły wbudowane w organizatora i pokazane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a5875-137">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>  
  
- <span data-ttu-id="a5875-138">Inne obiekty, które muszą jawnie kontrolować zachowanie organizowania, mogą implementować <xref:System.IConvertible> interfejs.</span><span class="sxs-lookup"><span data-stu-id="a5875-138">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="a5875-139">W takim przypadku typ Variant jest określany przez kod typu zwracany <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> przez metodę.</span><span class="sxs-lookup"><span data-stu-id="a5875-139">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5875-140">W przeciwnym razie obiekt jest zorganizowany jako wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="a5875-140">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>  
  
### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="a5875-141">Kierowanie typów systemu do wariantu</span><span class="sxs-lookup"><span data-stu-id="a5875-141">Marshaling System Types to Variant</span></span>  
 <span data-ttu-id="a5875-142">W poniższej tabeli przedstawiono typy obiektów zarządzanych i odpowiadające im typy wariantów COM.</span><span class="sxs-lookup"><span data-stu-id="a5875-142">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="a5875-143">Te typy są konwertowane tylko wtedy, gdy podpis wywoływanej metody jest typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5875-143">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
|<span data-ttu-id="a5875-144">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="a5875-144">Object type</span></span>|<span data-ttu-id="a5875-145">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="a5875-145">COM variant type</span></span>|  
|-----------------|----------------------|  
|<span data-ttu-id="a5875-146">Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a5875-146">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="a5875-147">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a5875-147">**VT_EMPTY**</span></span>|  
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="a5875-148">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a5875-148">**VT_NULL**</span></span>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="a5875-149">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a5875-149">**VT_ERROR**</span></span>|  
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="a5875-150">**VT_ERROR** z **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="a5875-150">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="a5875-151">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="a5875-151">**VT_DISPATCH**</span></span>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="a5875-152">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a5875-152">**VT_UNKNOWN**</span></span>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="a5875-153">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a5875-153">**VT_CY**</span></span>|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="a5875-154">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a5875-154">**VT_BOOL**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="a5875-155">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a5875-155">**VT_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="a5875-156">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a5875-156">**VT_UI1**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="a5875-157">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a5875-157">**VT_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="a5875-158">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a5875-158">**VT_UI2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="a5875-159">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a5875-159">**VT_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="a5875-160">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a5875-160">**VT_UI4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="a5875-161">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a5875-161">**VT_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="a5875-162">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a5875-162">**VT_UI8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="a5875-163">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a5875-163">**VT_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="a5875-164">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a5875-164">**VT_R8**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="a5875-165">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a5875-165">**VT_DECIMAL**</span></span>|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="a5875-166">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a5875-166">**VT_DATE**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="a5875-167">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a5875-167">**VT_BSTR**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="a5875-168">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a5875-168">**VT_INT**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="a5875-169">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a5875-169">**VT_UINT**</span></span>|  
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="a5875-170">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a5875-170">**VT_ARRAY**</span></span>|  
  
 <span data-ttu-id="a5875-171">Korzystając z `MarshalObject` interfejsu zdefiniowanego w poprzednim przykładzie, Poniższy przykład kodu demonstruje, jak przekazać różne typy wariantów do serwera com.</span><span class="sxs-lookup"><span data-stu-id="a5875-171">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="a5875-172">Typy com, które nie mają odpowiednich typów zarządzanych, mogą być organizowane przy użyciu klas otoki <xref:System.Runtime.InteropServices.ErrorWrapper> <xref:System.Runtime.InteropServices.UnknownWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>takich jak, <xref:System.Runtime.InteropServices.CurrencyWrapper>, i.</span><span class="sxs-lookup"><span data-stu-id="a5875-172">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="a5875-173">Poniższy przykład kodu demonstruje, jak używać tych otok do przekazywania różnych typów wariantów do serwera COM.</span><span class="sxs-lookup"><span data-stu-id="a5875-173">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>  
  
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
  
 <span data-ttu-id="a5875-174">Klasy otoki są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a5875-174">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="a5875-175">Kierowanie interfejsu obiektem IConvertible do wariantu</span><span class="sxs-lookup"><span data-stu-id="a5875-175">Marshaling the IConvertible Interface to Variant</span></span>  
 <span data-ttu-id="a5875-176">Typy inne niż wymienione w poprzedniej sekcji mogą kontrolować sposób, w jaki są one organizowane przez implementację <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a5875-176">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="a5875-177">Jeśli obiekt implementuje interfejs **obiektem IConvertible** , typ Variant com jest określany w czasie wykonywania przez wartość <xref:System.TypeCode> <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> wyliczenia zwracanego z metody.</span><span class="sxs-lookup"><span data-stu-id="a5875-177">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a5875-178">W poniższej tabeli przedstawiono możliwe wartości wyliczenia elementu **TypeCode** i odpowiedni typ modelu COM dla każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="a5875-178">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>  
  
|<span data-ttu-id="a5875-179">TypeCode</span><span class="sxs-lookup"><span data-stu-id="a5875-179">TypeCode</span></span>|<span data-ttu-id="a5875-180">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="a5875-180">COM variant type</span></span>|  
|--------------|----------------------|  
|<span data-ttu-id="a5875-181">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="a5875-181">**TypeCode.Empty**</span></span>|<span data-ttu-id="a5875-182">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a5875-182">**VT_EMPTY**</span></span>|  
|<span data-ttu-id="a5875-183">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="a5875-183">**TypeCode.Object**</span></span>|<span data-ttu-id="a5875-184">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a5875-184">**VT_UNKNOWN**</span></span>|  
|<span data-ttu-id="a5875-185">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="a5875-185">**TypeCode.DBNull**</span></span>|<span data-ttu-id="a5875-186">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a5875-186">**VT_NULL**</span></span>|  
|<span data-ttu-id="a5875-187">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="a5875-187">**TypeCode.Boolean**</span></span>|<span data-ttu-id="a5875-188">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a5875-188">**VT_BOOL**</span></span>|  
|<span data-ttu-id="a5875-189">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="a5875-189">**TypeCode.Char**</span></span>|<span data-ttu-id="a5875-190">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a5875-190">**VT_UI2**</span></span>|  
|<span data-ttu-id="a5875-191">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="a5875-191">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="a5875-192">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a5875-192">**VT_I1**</span></span>|  
|<span data-ttu-id="a5875-193">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="a5875-193">**TypeCode.Byte**</span></span>|<span data-ttu-id="a5875-194">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a5875-194">**VT_UI1**</span></span>|  
|<span data-ttu-id="a5875-195">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="a5875-195">**TypeCode.Int16**</span></span>|<span data-ttu-id="a5875-196">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a5875-196">**VT_I2**</span></span>|  
|<span data-ttu-id="a5875-197">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="a5875-197">**TypeCode.UInt16**</span></span>|<span data-ttu-id="a5875-198">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a5875-198">**VT_UI2**</span></span>|  
|<span data-ttu-id="a5875-199">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="a5875-199">**TypeCode.Int32**</span></span>|<span data-ttu-id="a5875-200">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a5875-200">**VT_I4**</span></span>|  
|<span data-ttu-id="a5875-201">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="a5875-201">**TypeCode.UInt32**</span></span>|<span data-ttu-id="a5875-202">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a5875-202">**VT_UI4**</span></span>|  
|<span data-ttu-id="a5875-203">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="a5875-203">**TypeCode.Int64**</span></span>|<span data-ttu-id="a5875-204">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a5875-204">**VT_I8**</span></span>|  
|<span data-ttu-id="a5875-205">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="a5875-205">**TypeCode.UInt64**</span></span>|<span data-ttu-id="a5875-206">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a5875-206">**VT_UI8**</span></span>|  
|<span data-ttu-id="a5875-207">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="a5875-207">**TypeCode.Single**</span></span>|<span data-ttu-id="a5875-208">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a5875-208">**VT_R4**</span></span>|  
|<span data-ttu-id="a5875-209">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="a5875-209">**TypeCode.Double**</span></span>|<span data-ttu-id="a5875-210">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a5875-210">**VT_R8**</span></span>|  
|<span data-ttu-id="a5875-211">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="a5875-211">**TypeCode.Decimal**</span></span>|<span data-ttu-id="a5875-212">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a5875-212">**VT_DECIMAL**</span></span>|  
|<span data-ttu-id="a5875-213">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="a5875-213">**TypeCode.DateTime**</span></span>|<span data-ttu-id="a5875-214">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a5875-214">**VT_DATE**</span></span>|  
|<span data-ttu-id="a5875-215">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="a5875-215">**TypeCode.String**</span></span>|<span data-ttu-id="a5875-216">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a5875-216">**VT_BSTR**</span></span>|  
|<span data-ttu-id="a5875-217">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-217">Not supported.</span></span>|<span data-ttu-id="a5875-218">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a5875-218">**VT_INT**</span></span>|  
|<span data-ttu-id="a5875-219">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-219">Not supported.</span></span>|<span data-ttu-id="a5875-220">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a5875-220">**VT_UINT**</span></span>|  
|<span data-ttu-id="a5875-221">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-221">Not supported.</span></span>|<span data-ttu-id="a5875-222">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="a5875-222">**VT_ARRAY**</span></span>|  
|<span data-ttu-id="a5875-223">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-223">Not supported.</span></span>|<span data-ttu-id="a5875-224">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="a5875-224">**VT_RECORD**</span></span>|  
|<span data-ttu-id="a5875-225">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-225">Not supported.</span></span>|<span data-ttu-id="a5875-226">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a5875-226">**VT_CY**</span></span>|  
|<span data-ttu-id="a5875-227">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-227">Not supported.</span></span>|<span data-ttu-id="a5875-228">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="a5875-228">**VT_VARIANT**</span></span>|  
  
 <span data-ttu-id="a5875-229">Wartość wariantu COM jest określana przez wywołanie interfejsu typu **IConvertible.to** , gdzie **do** *typu* jest procedura konwersji odpowiadająca typowi zwróconemu z **obiektem IConvertible. GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="a5875-229">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="a5875-230">Na przykład obiekt, który zwraca element **TypeCode. Double** z **obiektem IConvertible. GetTypeCode** jest zorganizowany jako wariant modelu COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="a5875-230">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="a5875-231">Można uzyskać wartość wariantu (przechowywaną w polu **dblVal** wariantu com) przez rzutowanie do interfejsu **obiektem IConvertible** <xref:System.IConvertible.ToDouble%2A> i wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="a5875-231">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>  
  
## <a name="marshaling-variant-to-object"></a><span data-ttu-id="a5875-232">Kierowanie elementu Variant do obiektu</span><span class="sxs-lookup"><span data-stu-id="a5875-232">Marshaling Variant to Object</span></span>  
 <span data-ttu-id="a5875-233">Podczas organizowania elementu Variant z obiektem, typu i czasami wartość, z której jest zorganizowany, określa typ utworzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5875-233">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="a5875-234">W poniższej tabeli przedstawiono każdy typ wariantu i odpowiedni typ obiektu, który organizator tworzy, gdy wariant jest przekazywany z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5875-234">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>  
  
|<span data-ttu-id="a5875-235">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="a5875-235">COM variant type</span></span>|<span data-ttu-id="a5875-236">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="a5875-236">Object type</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a5875-237">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="a5875-237">**VT_EMPTY**</span></span>|<span data-ttu-id="a5875-238">Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a5875-238">Null object reference (**Nothing** in Visual Basic).</span></span>|  
|<span data-ttu-id="a5875-239">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="a5875-239">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-240">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="a5875-240">**VT_DISPATCH**</span></span>|<span data-ttu-id="a5875-241">**System. __ComObject** lub null, if (pdispVal = = null)</span><span class="sxs-lookup"><span data-stu-id="a5875-241">**System.__ComObject** or null if (pdispVal == null)</span></span>|  
|<span data-ttu-id="a5875-242">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="a5875-242">**VT_UNKNOWN**</span></span>|<span data-ttu-id="a5875-243">**System. __ComObject** lub null, if (punkVal = = null)</span><span class="sxs-lookup"><span data-stu-id="a5875-243">**System.__ComObject** or null if (punkVal == null)</span></span>|  
|<span data-ttu-id="a5875-244">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="a5875-244">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-245">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="a5875-245">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-246">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="a5875-246">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-247">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="a5875-247">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-248">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="a5875-248">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-249">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="a5875-249">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-250">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="a5875-250">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-251">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="a5875-251">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-252">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="a5875-252">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-253">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="a5875-253">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-254">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="a5875-254">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-255">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="a5875-255">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-256">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="a5875-256">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-257">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="a5875-257">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-258">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="a5875-258">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-259">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="a5875-259">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-260">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="a5875-260">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-261">**VT_ARRAY** &#124; **VT_** \*</span><span class="sxs-lookup"><span data-stu-id="a5875-261">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-262">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="a5875-262">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|  
|<span data-ttu-id="a5875-263">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="a5875-263">**VT_RECORD**</span></span>|<span data-ttu-id="a5875-264">Odpowiedni opakowany typ wartości.</span><span class="sxs-lookup"><span data-stu-id="a5875-264">Corresponding boxed value type.</span></span>|  
|<span data-ttu-id="a5875-265">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="a5875-265">**VT_VARIANT**</span></span>|<span data-ttu-id="a5875-266">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5875-266">Not supported.</span></span>|  
  
 <span data-ttu-id="a5875-267">Typy wariantów przesyłane z modelu COM do kodu zarządzanego, a następnie z powrotem do modelu COM mogą nie zachować tego samego typu wariantu dla czasu trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5875-267">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="a5875-268">Rozważ, co się dzieje, gdy wariant typu **VT_DISPATCH** zostanie przekazana z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a5875-268">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="a5875-269">Podczas organizowania wariant jest konwertowany na <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a5875-269">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a5875-270">Jeśli **obiekt** jest następnie przekazywany z powrotem do modelu COM, jest on zorganizowany z powrotem do wariantu typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="a5875-270">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="a5875-271">Nie ma gwarancji, że wariant utworzony, gdy obiekt jest zorganizowany z kodu zarządzanego do modelu COM, będzie tego samego typu co wariant użyty początkowo do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5875-271">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>  
  
## <a name="marshaling-byref-variants"></a><span data-ttu-id="a5875-272">Kierowanie wariantów ByRef</span><span class="sxs-lookup"><span data-stu-id="a5875-272">Marshaling ByRef Variants</span></span>  
 <span data-ttu-id="a5875-273">Chociaż warianty mogą być przesyłane przez wartość lub przez odwołanie, flaga **VT_BYREF** może być również używana z dowolnym typem VARIANT, aby wskazać, że zawartość wariantu jest przesyłana przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="a5875-273">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="a5875-274">Różnica między organizowaniem wariantów według odwołania i kierowaniem wariantów z zestawem flag **VT_BYREF** może być myląca.</span><span class="sxs-lookup"><span data-stu-id="a5875-274">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="a5875-275">Na poniższej ilustracji objaśniono różnice:</span><span class="sxs-lookup"><span data-stu-id="a5875-275">The following illustration clarifies the differences:</span></span>  
  
 ![Diagram pokazujący wariant zakończony przez stos.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)  
<span data-ttu-id="a5875-277">Warianty przenoszone przez wartość i przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="a5875-277">Variants passed by value and by reference</span></span>  
  
 <span data-ttu-id="a5875-278">**Domyślne zachowanie dla organizowania obiektów i wariantów według wartości**</span><span class="sxs-lookup"><span data-stu-id="a5875-278">**Default behavior for marshaling objects and variants by value**</span></span>  
  
- <span data-ttu-id="a5875-279">Podczas przekazywania obiektów z kodu zarządzanego do modelu COM zawartość obiektu jest kopiowana do nowego wariantu utworzonego przez organizatora przy użyciu reguł zdefiniowanych w [kierowaniu obiektu do wariantu](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="a5875-279">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="a5875-280">Zmiany wprowadzone do wariantu po stronie niezarządzanej nie są propagowane z powrotem do oryginalnego obiektu po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5875-280">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>  
  
- <span data-ttu-id="a5875-281">Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariantu jest kopiowana do nowo utworzonego obiektu, przy użyciu reguł zdefiniowanych w [kierowaniu wariantu do obiektu](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="a5875-281">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="a5875-282">Zmiany wprowadzone do obiektu na stronie zarządzanej nie są propagowane z powrotem do oryginalnego wariantu w przypadku powrotu z wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5875-282">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>  
  
 <span data-ttu-id="a5875-283">**Domyślne zachowanie dla organizowania obiektów i wariantów według odwołania**</span><span class="sxs-lookup"><span data-stu-id="a5875-283">**Default behavior for marshaling objects and variants by reference**</span></span>  
  
 <span data-ttu-id="a5875-284">Aby propagować zmiany z powrotem do obiektu wywołującego, parametry muszą być przesyłane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-284">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="a5875-285">Można na przykład użyć słowa kluczowego **ref** w C# (lub **ByRef** w Visual Basic kodzie zarządzanym) do przekazywania parametrów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-285">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="a5875-286">W modelu COM parametry odwołania są przesyłane przy użyciu wskaźnika, takiego jak **Variant \*** .</span><span class="sxs-lookup"><span data-stu-id="a5875-286">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>  
  
- <span data-ttu-id="a5875-287">Podczas przekazywania obiektu do modelu COM przez odwołanie organizator tworzy nowy wariant i kopiuje zawartość odwołania do obiektu do wariantu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="a5875-287">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="a5875-288">Wariant jest przesyłany do niezarządzanej funkcji, w której użytkownik może zmienić zawartość wariantu.</span><span class="sxs-lookup"><span data-stu-id="a5875-288">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="a5875-289">W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do wariantu po stronie niezarządzanej są propagowane do oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a5875-289">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="a5875-290">Jeśli Typ wariantu różni się od typu wariantu przekazanego do wywołania, zmiany są propagowane z powrotem do obiektu innego typu.</span><span class="sxs-lookup"><span data-stu-id="a5875-290">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="a5875-291">Oznacza to, że typ obiektu, który został przesłany do wywołania może różnić się od typu obiektu zwróconego przez wywołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-291">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>  
  
- <span data-ttu-id="a5875-292">Podczas przekazywania wariantu do kodu zarządzanego przez odwołanie organizator tworzy nowy obiekt i kopiuje zawartość wariantu do obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="a5875-292">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="a5875-293">Odwołanie do obiektu jest przesyłane do funkcji zarządzanej, gdzie użytkownik może zmienić obiekt.</span><span class="sxs-lookup"><span data-stu-id="a5875-293">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="a5875-294">W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do przywoływanego obiektu są propagowane z powrotem do oryginalnego wariantu.</span><span class="sxs-lookup"><span data-stu-id="a5875-294">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="a5875-295">Jeśli typ obiektu różni się od typu obiektu przekazanego do wywołania, typ oryginalnego wariantu zostanie zmieniony, a wartość jest propagowana z powrotem do wariantu.</span><span class="sxs-lookup"><span data-stu-id="a5875-295">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="a5875-296">Ponownie Typ wariantu przekazana do wywołania może różnić się od typu wariantu zwróconego przez wywołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-296">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>  
  
 <span data-ttu-id="a5875-297">**Domyślne zachowanie organizowania elementu Variant z ustawioną flagą VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="a5875-297">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>  
  
- <span data-ttu-id="a5875-298">Wariant, który jest przesyłany do kodu zarządzanego przez wartość, może mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera odwołanie zamiast wartości.</span><span class="sxs-lookup"><span data-stu-id="a5875-298">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="a5875-299">W takim przypadku wariant jest nadal kierowany do obiektu, ponieważ wariant jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="a5875-299">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="a5875-300">Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="a5875-300">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="a5875-301">Obiekt jest następnie przekazywać do zarządzanej funkcji; Jednak po powrocie z wywołania obiekt nie jest propagowany z powrotem do oryginalnego wariantu.</span><span class="sxs-lookup"><span data-stu-id="a5875-301">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="a5875-302">Zmiany wprowadzone w obiekcie zarządzanym zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="a5875-302">Changes made to the managed object are lost.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="a5875-303">Nie ma możliwości zmiany wartości wariantu przekazaną przez wartość, nawet jeśli wariant ma ustawioną flagę **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="a5875-303">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>  
  
- <span data-ttu-id="a5875-304">Wariant przesyłany do kodu zarządzanego przez odwołanie może również mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera inne odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-304">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="a5875-305">Jeśli tak, wariant jest zorganizowany do obiektu **ref** , ponieważ wariant jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a5875-305">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="a5875-306">Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="a5875-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="a5875-307">W przypadku powrotu z wywołania, wartość obiektu jest propagowana z powrotem do odwołania w obrębie oryginalnego wariantu tylko wtedy, gdy obiekt jest tego samego typu co obiekt przekazane.</span><span class="sxs-lookup"><span data-stu-id="a5875-307">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="a5875-308">Oznacza to, że propagacja nie zmienia typu elementu Variant z ustawioną flagą **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="a5875-308">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="a5875-309">Jeśli typ obiektu zostanie zmieniony podczas wywołania, <xref:System.InvalidCastException> występuje po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="a5875-309">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>  
  
 <span data-ttu-id="a5875-310">Poniższa tabela podsumowuje reguły propagacji dla wariantów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="a5875-310">The following table summarizes the propagation rules for variants and objects.</span></span>  
  
|<span data-ttu-id="a5875-311">Z</span><span class="sxs-lookup"><span data-stu-id="a5875-311">From</span></span>|<span data-ttu-id="a5875-312">Zadanie</span><span class="sxs-lookup"><span data-stu-id="a5875-312">To</span></span>|<span data-ttu-id="a5875-313">Zmiany rozpropagowane</span><span class="sxs-lookup"><span data-stu-id="a5875-313">Changes propagated back</span></span>|  
|----------|--------|-----------------------------|  
|<span data-ttu-id="a5875-314">**Typ Variant** *v*</span><span class="sxs-lookup"><span data-stu-id="a5875-314">**Variant**  *v*</span></span>|<span data-ttu-id="a5875-315">**Obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-315">**Object**  *o*</span></span>|<span data-ttu-id="a5875-316">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="a5875-316">Never</span></span>|  
|<span data-ttu-id="a5875-317">**Obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-317">**Object**  *o*</span></span>|<span data-ttu-id="a5875-318">**Typ Variant** *v*</span><span class="sxs-lookup"><span data-stu-id="a5875-318">**Variant**  *v*</span></span>|<span data-ttu-id="a5875-319">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="a5875-319">Never</span></span>|  
|<span data-ttu-id="a5875-320">**Variant**  ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="a5875-320">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="a5875-321">**Ref — obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-321">**Ref Object**  *o*</span></span>|<span data-ttu-id="a5875-322">zawsze</span><span class="sxs-lookup"><span data-stu-id="a5875-322">Always</span></span>|  
|<span data-ttu-id="a5875-323">**Ref — obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-323">**Ref object**  *o*</span></span>|<span data-ttu-id="a5875-324">**Variant**  ***\****  *pv*</span><span class="sxs-lookup"><span data-stu-id="a5875-324">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="a5875-325">zawsze</span><span class="sxs-lookup"><span data-stu-id="a5875-325">Always</span></span>|  
|<span data-ttu-id="a5875-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="a5875-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="a5875-327">**Obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-327">**Object**  *o*</span></span>|<span data-ttu-id="a5875-328">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="a5875-328">Never</span></span>|  
|<span data-ttu-id="a5875-329">**Typ Variant** *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="a5875-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="a5875-330">**Ref — obiekt** *o*</span><span class="sxs-lookup"><span data-stu-id="a5875-330">**Ref Object**  *o*</span></span>|<span data-ttu-id="a5875-331">Tylko wtedy, gdy typ nie został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="a5875-331">Only if the type has not changed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5875-332">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5875-332">See also</span></span>

- [<span data-ttu-id="a5875-333">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="a5875-333">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="a5875-334">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="a5875-334">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="a5875-335">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a5875-335">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="a5875-336">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="a5875-336">Copying and Pinning</span></span>](copying-and-pinning.md)
