---
title: Domyślny marshaling dla obiektów
description: Zrozumienie domyślnego kierowania dla obiektów. Przejrzyj opcje organizowania. Kierowanie obiektów do interfejsów lub wariantów, wariantów do obiektów i wariantów typu ByRef.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 7b8f94f4dfd8e8b9e8e04df8de5f8266a8581a92
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618457"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="6bf82-105">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="6bf82-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="6bf82-106">Parametry i pola, które <xref:System.Object?displayProperty=nameWithType> zostały wpisane jako mogą być ujawnione w kodzie niezarządzanym jako jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="6bf82-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="6bf82-107">Wariant, gdy obiekt jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="6bf82-108">Interfejs, gdy obiekt jest polem struktury.</span><span class="sxs-lookup"><span data-stu-id="6bf82-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="6bf82-109">Tylko usługa międzyoperacyjna modelu COM obsługuje kierowanie dla typów obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bf82-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="6bf82-110">Domyślnym zachowaniem jest kierowanie obiektów do wariantów COM.</span><span class="sxs-lookup"><span data-stu-id="6bf82-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="6bf82-111">Te reguły mają zastosowanie tylko do **obiektu** typu i nie mają zastosowania do obiektów silnie wpisanych, które pochodzą z klasy **Object** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="6bf82-112">Opcje organizowania</span><span class="sxs-lookup"><span data-stu-id="6bf82-112">Marshaling Options</span></span>

<span data-ttu-id="6bf82-113">W poniższej tabeli przedstawiono opcje organizowania dla typu danych **obiekt** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="6bf82-114">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bf82-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="6bf82-115">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6bf82-115">Enumeration type</span></span>|<span data-ttu-id="6bf82-116">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="6bf82-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="6bf82-117">**UnmanagedType. struct**</span><span class="sxs-lookup"><span data-stu-id="6bf82-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="6bf82-118">(domyślnie dla parametrów)</span><span class="sxs-lookup"><span data-stu-id="6bf82-118">(default for parameters)</span></span>|<span data-ttu-id="6bf82-119">Wariant w stylu COM.</span><span class="sxs-lookup"><span data-stu-id="6bf82-119">A COM-style variant.</span></span>|
|<span data-ttu-id="6bf82-120">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="6bf82-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="6bf82-121">Interfejs **IDispatch** , o ile to możliwe; w przeciwnym razie interfejs **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="6bf82-122">**UnmanagedType. IUnknown**</span><span class="sxs-lookup"><span data-stu-id="6bf82-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="6bf82-123">(domyślnie dla pól)</span><span class="sxs-lookup"><span data-stu-id="6bf82-123">(default for fields)</span></span>|<span data-ttu-id="6bf82-124">Interfejs **IUnknown** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="6bf82-125">**UnmanagedType. IDispatch**</span><span class="sxs-lookup"><span data-stu-id="6bf82-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="6bf82-126">Interfejs **IDispatch** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="6bf82-127">W poniższym przykładzie przedstawiono definicję interfejsu zarządzanego dla programu `MarshalObject` .</span><span class="sxs-lookup"><span data-stu-id="6bf82-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="6bf82-128">Poniższy kod eksportuje `MarshalObject` interfejs do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6bf82-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

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
> <span data-ttu-id="6bf82-129">Organizator międzyoperacyjny automatycznie zwalnia wszelki przydzielony obiekt wewnątrz wariantu po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="6bf82-130">Poniższy przykład przedstawia sformatowany typ wartości.</span><span class="sxs-lookup"><span data-stu-id="6bf82-130">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="6bf82-131">Poniższy kod eksportuje sformatowany typ do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6bf82-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="6bf82-132">Kierowanie obiektu do interfejsu</span><span class="sxs-lookup"><span data-stu-id="6bf82-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="6bf82-133">Gdy obiekt jest uwidaczniany w modelu COM jako interfejs, ten interfejs jest interfejsem klasy dla zarządzanego typu <xref:System.Object> ( **_object** interfejs).</span><span class="sxs-lookup"><span data-stu-id="6bf82-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="6bf82-134">Ten interfejs jest wpisywany jako **IDispatch** ( <xref:System.Runtime.InteropServices.UnmanagedType> ) lub **IUnknown** (**UnmanagedType. IUnknown**) w bibliotece typów będących wynikiem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="6bf82-135">Klienci modelu COM mogą dynamicznie wywoływać elementy członkowskie zarządzanej klasy lub wszelkich członków wdrożonych przez klasy pochodne za pomocą interfejsu **_object** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="6bf82-136">Klient może również wywołać metodę **QueryInterface** , aby uzyskać inny interfejs jawnie zaimplementowany przez typ zarządzany.</span><span class="sxs-lookup"><span data-stu-id="6bf82-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="6bf82-137">Kierowanie obiektu do wariantu</span><span class="sxs-lookup"><span data-stu-id="6bf82-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="6bf82-138">Gdy obiekt jest zorganizowany do wariantu, wewnętrzny typ Variant jest określany w czasie wykonywania na podstawie następujących reguł:</span><span class="sxs-lookup"><span data-stu-id="6bf82-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="6bf82-139">Jeśli odwołanie do obiektu ma wartość null (**Nothing** w Visual Basic), obiekt jest zorganizowany do wariantu typu **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="6bf82-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="6bf82-140">Jeśli obiekt jest wystąpieniem dowolnego typu wymienionych w poniższej tabeli, wynikowy typ Variant jest określany przez reguły wbudowane w organizatora i pokazane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="6bf82-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="6bf82-141">Inne obiekty, które muszą jawnie kontrolować zachowanie organizowania, mogą implementować <xref:System.IConvertible> interfejs.</span><span class="sxs-lookup"><span data-stu-id="6bf82-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="6bf82-142">W takim przypadku typ Variant jest określany przez kod typu zwracany przez <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="6bf82-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6bf82-143">W przeciwnym razie obiekt jest zorganizowany jako wariant typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="6bf82-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="6bf82-144">Kierowanie typów systemu do wariantu</span><span class="sxs-lookup"><span data-stu-id="6bf82-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="6bf82-145">W poniższej tabeli przedstawiono typy obiektów zarządzanych i odpowiadające im typy wariantów COM.</span><span class="sxs-lookup"><span data-stu-id="6bf82-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="6bf82-146">Te typy są konwertowane tylko wtedy, gdy podpis wywoływanej metody jest typu <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bf82-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="6bf82-147">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="6bf82-147">Object type</span></span>|<span data-ttu-id="6bf82-148">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="6bf82-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="6bf82-149">Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6bf82-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="6bf82-150">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="6bf82-151">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="6bf82-152">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="6bf82-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="6bf82-153">**VT_ERROR** z **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="6bf82-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="6bf82-154">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="6bf82-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="6bf82-155">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="6bf82-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="6bf82-156">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="6bf82-157">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="6bf82-158">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="6bf82-159">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="6bf82-160">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="6bf82-161">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="6bf82-162">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="6bf82-163">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="6bf82-164">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="6bf82-165">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="6bf82-166">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="6bf82-167">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="6bf82-168">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="6bf82-169">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="6bf82-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="6bf82-170">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="6bf82-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="6bf82-171">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="6bf82-172">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="6bf82-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="6bf82-174">Korzystając z `MarshalObject` interfejsu zdefiniowanego w poprzednim przykładzie, Poniższy przykład kodu demonstruje, jak przekazać różne typy wariantów do serwera com.</span><span class="sxs-lookup"><span data-stu-id="6bf82-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="6bf82-175">Typy com, które nie mają odpowiednich typów zarządzanych, mogą być organizowane przy użyciu klas otoki <xref:System.Runtime.InteropServices.ErrorWrapper> , takich jak,, <xref:System.Runtime.InteropServices.DispatchWrapper> <xref:System.Runtime.InteropServices.UnknownWrapper> i <xref:System.Runtime.InteropServices.CurrencyWrapper> .</span><span class="sxs-lookup"><span data-stu-id="6bf82-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="6bf82-176">Poniższy przykład kodu demonstruje, jak używać tych otok do przekazywania różnych typów wariantów do serwera COM.</span><span class="sxs-lookup"><span data-stu-id="6bf82-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="6bf82-177">Klasy otoki są zdefiniowane w <xref:System.Runtime.InteropServices> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6bf82-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="6bf82-178">Kierowanie interfejsu obiektem IConvertible do wariantu</span><span class="sxs-lookup"><span data-stu-id="6bf82-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="6bf82-179">Typy inne niż wymienione w poprzedniej sekcji mogą kontrolować sposób, w jaki są one organizowane przez implementację <xref:System.IConvertible> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="6bf82-180">Jeśli obiekt implementuje interfejs **obiektem IConvertible** , typ Variant com jest określany w czasie wykonywania przez wartość <xref:System.TypeCode> wyliczenia zwracanego z <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6bf82-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6bf82-181">W poniższej tabeli przedstawiono możliwe wartości wyliczenia elementu **TypeCode** i odpowiedni typ modelu COM dla każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="6bf82-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="6bf82-182">Elementu TypeCode</span><span class="sxs-lookup"><span data-stu-id="6bf82-182">TypeCode</span></span>|<span data-ttu-id="6bf82-183">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="6bf82-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="6bf82-184">**TypeCode. Empty**</span><span class="sxs-lookup"><span data-stu-id="6bf82-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="6bf82-185">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="6bf82-186">**TypeCode. Object**</span><span class="sxs-lookup"><span data-stu-id="6bf82-186">**TypeCode.Object**</span></span>|<span data-ttu-id="6bf82-187">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="6bf82-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="6bf82-188">**TypeCode. DBNull**</span><span class="sxs-lookup"><span data-stu-id="6bf82-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="6bf82-189">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-189">**VT_NULL**</span></span>|
|<span data-ttu-id="6bf82-190">**TypeCode. Boolean**</span><span class="sxs-lookup"><span data-stu-id="6bf82-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="6bf82-191">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="6bf82-192">**TypeCode. Char**</span><span class="sxs-lookup"><span data-stu-id="6bf82-192">**TypeCode.Char**</span></span>|<span data-ttu-id="6bf82-193">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-193">**VT_UI2**</span></span>|
|<span data-ttu-id="6bf82-194">**TypeCode. nadana**</span><span class="sxs-lookup"><span data-stu-id="6bf82-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="6bf82-195">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-195">**VT_I1**</span></span>|
|<span data-ttu-id="6bf82-196">**TypeCode. Byte**</span><span class="sxs-lookup"><span data-stu-id="6bf82-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="6bf82-197">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-197">**VT_UI1**</span></span>|
|<span data-ttu-id="6bf82-198">**TypeCode. Int16**</span><span class="sxs-lookup"><span data-stu-id="6bf82-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="6bf82-199">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-199">**VT_I2**</span></span>|
|<span data-ttu-id="6bf82-200">**TypeCode. UInt16**</span><span class="sxs-lookup"><span data-stu-id="6bf82-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="6bf82-201">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-201">**VT_UI2**</span></span>|
|<span data-ttu-id="6bf82-202">**TypeCode. Int32**</span><span class="sxs-lookup"><span data-stu-id="6bf82-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="6bf82-203">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-203">**VT_I4**</span></span>|
|<span data-ttu-id="6bf82-204">**TypeCode. UInt32**</span><span class="sxs-lookup"><span data-stu-id="6bf82-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="6bf82-205">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-205">**VT_UI4**</span></span>|
|<span data-ttu-id="6bf82-206">**TypeCode. Int64**</span><span class="sxs-lookup"><span data-stu-id="6bf82-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="6bf82-207">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-207">**VT_I8**</span></span>|
|<span data-ttu-id="6bf82-208">**TypeCode. UInt64**</span><span class="sxs-lookup"><span data-stu-id="6bf82-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="6bf82-209">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-209">**VT_UI8**</span></span>|
|<span data-ttu-id="6bf82-210">**TypeCode. Single**</span><span class="sxs-lookup"><span data-stu-id="6bf82-210">**TypeCode.Single**</span></span>|<span data-ttu-id="6bf82-211">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-211">**VT_R4**</span></span>|
|<span data-ttu-id="6bf82-212">**TypeCode. Double**</span><span class="sxs-lookup"><span data-stu-id="6bf82-212">**TypeCode.Double**</span></span>|<span data-ttu-id="6bf82-213">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-213">**VT_R8**</span></span>|
|<span data-ttu-id="6bf82-214">**TypeCode. Decimal**</span><span class="sxs-lookup"><span data-stu-id="6bf82-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="6bf82-215">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="6bf82-216">**TypeCode. DateTime**</span><span class="sxs-lookup"><span data-stu-id="6bf82-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="6bf82-217">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="6bf82-217">**VT_DATE**</span></span>|
|<span data-ttu-id="6bf82-218">**TypeCode. String**</span><span class="sxs-lookup"><span data-stu-id="6bf82-218">**TypeCode.String**</span></span>|<span data-ttu-id="6bf82-219">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="6bf82-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="6bf82-220">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-220">Not supported.</span></span>|<span data-ttu-id="6bf82-221">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-221">**VT_INT**</span></span>|
|<span data-ttu-id="6bf82-222">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-222">Not supported.</span></span>|<span data-ttu-id="6bf82-223">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-223">**VT_UINT**</span></span>|
|<span data-ttu-id="6bf82-224">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-224">Not supported.</span></span>|<span data-ttu-id="6bf82-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="6bf82-226">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-226">Not supported.</span></span>|<span data-ttu-id="6bf82-227">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="6bf82-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="6bf82-228">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-228">Not supported.</span></span>|<span data-ttu-id="6bf82-229">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-229">**VT_CY**</span></span>|
|<span data-ttu-id="6bf82-230">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-230">Not supported.</span></span>|<span data-ttu-id="6bf82-231">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="6bf82-232">Wartość wariantu COM jest określana przez wywołanie interfejsu typu **IConvertible.to** *Type* , gdzie **do** *typu* jest procedura konwersji odpowiadająca typowi zwróconemu z **obiektem IConvertible. GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="6bf82-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="6bf82-233">Na przykład obiekt, który zwraca element **TypeCode. Double** z **obiektem IConvertible. GetTypeCode** jest zorganizowany jako wariant modelu COM typu **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="6bf82-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="6bf82-234">Można uzyskać wartość wariantu (przechowywaną w polu **dblVal** wariantu com) przez rzutowanie do interfejsu **obiektem IConvertible** i wywołanie <xref:System.IConvertible.ToDouble%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6bf82-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="6bf82-235">Kierowanie elementu Variant do obiektu</span><span class="sxs-lookup"><span data-stu-id="6bf82-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="6bf82-236">Podczas organizowania elementu Variant z obiektem, typu i czasami wartość, z której jest zorganizowany, określa typ utworzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="6bf82-237">W poniższej tabeli przedstawiono każdy typ wariantu i odpowiedni typ obiektu, który organizator tworzy, gdy wariant jest przekazywany z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bf82-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="6bf82-238">Typ Variant COM</span><span class="sxs-lookup"><span data-stu-id="6bf82-238">COM variant type</span></span>|<span data-ttu-id="6bf82-239">Typ obiektu</span><span class="sxs-lookup"><span data-stu-id="6bf82-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="6bf82-240">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-240">**VT_EMPTY**</span></span>|<span data-ttu-id="6bf82-241">Odwołanie do obiektu o wartości null (**Nothing** w Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="6bf82-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="6bf82-242">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-243">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="6bf82-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="6bf82-244">**System. __ComObject** lub null, if (pdispVal = = null)</span><span class="sxs-lookup"><span data-stu-id="6bf82-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="6bf82-245">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="6bf82-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="6bf82-246">**System. __ComObject** lub null, if (punkVal = = null)</span><span class="sxs-lookup"><span data-stu-id="6bf82-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="6bf82-247">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="6bf82-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-248">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-249">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-250">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="6bf82-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-251">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-252">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="6bf82-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-253">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-254">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-255">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-256">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-257">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="6bf82-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-258">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="6bf82-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-259">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="6bf82-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-260">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="6bf82-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-261">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="6bf82-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-262">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-263">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-264">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="6bf82-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-265">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="6bf82-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="6bf82-266">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="6bf82-266">**VT_RECORD**</span></span>|<span data-ttu-id="6bf82-267">Odpowiedni opakowany typ wartości.</span><span class="sxs-lookup"><span data-stu-id="6bf82-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="6bf82-268">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="6bf82-268">**VT_VARIANT**</span></span>|<span data-ttu-id="6bf82-269">Nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-269">Not supported.</span></span>|

<span data-ttu-id="6bf82-270">Typy wariantów przesyłane z modelu COM do kodu zarządzanego, a następnie z powrotem do modelu COM mogą nie zachować tego samego typu wariantu dla czasu trwania wywołania.</span><span class="sxs-lookup"><span data-stu-id="6bf82-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="6bf82-271">Należy wziąć pod uwagę to, co się stanie, gdy wariant typu **VT_DISPATCH** jest przenoszona z modelu COM do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bf82-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="6bf82-272">Podczas organizowania wariant jest konwertowany na <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bf82-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6bf82-273">Jeśli **obiekt** jest następnie przekazywany z powrotem do modelu COM, jest on zorganizowany z powrotem do wariantu typu **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="6bf82-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="6bf82-274">Nie ma gwarancji, że wariant utworzony, gdy obiekt jest zorganizowany z kodu zarządzanego do modelu COM, będzie tego samego typu co wariant użyty początkowo do utworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="6bf82-275">Kierowanie wariantów ByRef</span><span class="sxs-lookup"><span data-stu-id="6bf82-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="6bf82-276">Chociaż warianty mogą być przesyłane przez wartość lub przez odwołanie, flaga **VT_BYREF** może być również używana z dowolnym typem VARIANT, aby wskazać, że zawartość wariantu jest przesyłana przez odwołanie, a nie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="6bf82-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="6bf82-277">Różnica między organizowaniem wariantów według odwołania i kierowaniem wariantów z zestawem flag **VT_BYREF** może być myląca.</span><span class="sxs-lookup"><span data-stu-id="6bf82-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="6bf82-278">Na poniższej ilustracji objaśniono różnice:</span><span class="sxs-lookup"><span data-stu-id="6bf82-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="6bf82-279">![Diagram pokazujący wariant zakończony przez stos.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="6bf82-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="6bf82-280">Warianty przenoszone przez wartość i przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="6bf82-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="6bf82-281">**Domyślne zachowanie dla organizowania obiektów i wariantów według wartości**</span><span class="sxs-lookup"><span data-stu-id="6bf82-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="6bf82-282">Podczas przekazywania obiektów z kodu zarządzanego do modelu COM zawartość obiektu jest kopiowana do nowego wariantu utworzonego przez organizatora przy użyciu reguł zdefiniowanych w [kierowaniu obiektu do wariantu](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="6bf82-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="6bf82-283">Zmiany wprowadzone do wariantu po stronie niezarządzanej nie są propagowane z powrotem do oryginalnego obiektu po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="6bf82-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="6bf82-284">Podczas przekazywania wariantów z modelu COM do kodu zarządzanego, zawartość wariantu jest kopiowana do nowo utworzonego obiektu, przy użyciu reguł zdefiniowanych w [kierowaniu wariantu do obiektu](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="6bf82-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="6bf82-285">Zmiany wprowadzone do obiektu na stronie zarządzanej nie są propagowane z powrotem do oryginalnego wariantu w przypadku powrotu z wywołania.</span><span class="sxs-lookup"><span data-stu-id="6bf82-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="6bf82-286">**Domyślne zachowanie dla organizowania obiektów i wariantów według odwołania**</span><span class="sxs-lookup"><span data-stu-id="6bf82-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="6bf82-287">Aby propagować zmiany z powrotem do obiektu wywołującego, parametry muszą być przesyłane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="6bf82-288">Można na przykład użyć słowa kluczowego **ref** w języku C# (lub **ByRef** w Visual Basic kodzie zarządzanym) do przekazywania parametrów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="6bf82-289">W modelu COM parametry odwołania są przesyłane przy użyciu wskaźnika, takiego jak \*\*Variant \* \*\*.</span><span class="sxs-lookup"><span data-stu-id="6bf82-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="6bf82-290">Podczas przekazywania obiektu do modelu COM przez odwołanie organizator tworzy nowy wariant i kopiuje zawartość odwołania do obiektu do wariantu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="6bf82-291">Wariant jest przesyłany do niezarządzanej funkcji, w której użytkownik może zmienić zawartość wariantu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="6bf82-292">W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do wariantu po stronie niezarządzanej są propagowane do oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="6bf82-293">Jeśli Typ wariantu różni się od typu wariantu przekazanego do wywołania, zmiany są propagowane z powrotem do obiektu innego typu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="6bf82-294">Oznacza to, że typ obiektu, który został przesłany do wywołania może różnić się od typu obiektu zwróconego przez wywołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="6bf82-295">Podczas przekazywania wariantu do kodu zarządzanego przez odwołanie organizator tworzy nowy obiekt i kopiuje zawartość wariantu do obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="6bf82-296">Odwołanie do obiektu jest przesyłane do funkcji zarządzanej, gdzie użytkownik może zmienić obiekt.</span><span class="sxs-lookup"><span data-stu-id="6bf82-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="6bf82-297">W przypadku powrotu z wywołania wszelkie zmiany wprowadzone do przywoływanego obiektu są propagowane z powrotem do oryginalnego wariantu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="6bf82-298">Jeśli typ obiektu różni się od typu obiektu przekazanego do wywołania, typ oryginalnego wariantu zostanie zmieniony, a wartość jest propagowana z powrotem do wariantu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="6bf82-299">Ponownie Typ wariantu przekazana do wywołania może różnić się od typu wariantu zwróconego przez wywołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="6bf82-300">**Domyślne zachowanie organizowania wariantu z ustawioną flagą VT_BYREF**</span><span class="sxs-lookup"><span data-stu-id="6bf82-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="6bf82-301">Wariant, który jest przesyłany do kodu zarządzanego przez wartość, może mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera odwołanie zamiast wartości.</span><span class="sxs-lookup"><span data-stu-id="6bf82-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="6bf82-302">W takim przypadku wariant jest nadal kierowany do obiektu, ponieważ wariant jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="6bf82-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="6bf82-303">Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="6bf82-304">Obiekt jest następnie przekazywać do zarządzanej funkcji; Jednak po powrocie z wywołania obiekt nie jest propagowany z powrotem do oryginalnego wariantu.</span><span class="sxs-lookup"><span data-stu-id="6bf82-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="6bf82-305">Zmiany wprowadzone w obiekcie zarządzanym zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="6bf82-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="6bf82-306">Nie ma możliwości zmiany wartości wariantu przekazaną przez wartość, nawet jeśli wariant ma ustawioną flagę **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="6bf82-307">Wariant jest przesyłany do kodu zarządzanego przez odwołanie może również mieć ustawioną flagę **VT_BYREF** , aby wskazać, że wariant zawiera inne odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="6bf82-308">Jeśli tak, wariant jest zorganizowany do obiektu **ref** , ponieważ wariant jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="6bf82-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="6bf82-309">Organizator automatycznie odwołuje się do zawartości wariantu i kopiuje go do nowo utworzonego obiektu przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="6bf82-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="6bf82-310">W przypadku powrotu z wywołania, wartość obiektu jest propagowana z powrotem do odwołania w obrębie oryginalnego wariantu tylko wtedy, gdy obiekt jest tego samego typu co obiekt przekazane.</span><span class="sxs-lookup"><span data-stu-id="6bf82-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="6bf82-311">Oznacza to, że propagacja nie zmienia typu wariantu z ustawioną flagą **VT_BYREF** .</span><span class="sxs-lookup"><span data-stu-id="6bf82-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="6bf82-312">Jeśli typ obiektu zostanie zmieniony podczas wywołania, <xref:System.InvalidCastException> występuje po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="6bf82-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="6bf82-313">Poniższa tabela podsumowuje reguły propagacji dla wariantów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bf82-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="6bf82-314">Z</span><span class="sxs-lookup"><span data-stu-id="6bf82-314">From</span></span>|<span data-ttu-id="6bf82-315">Do</span><span class="sxs-lookup"><span data-stu-id="6bf82-315">To</span></span>|<span data-ttu-id="6bf82-316">Zmiany rozpropagowane</span><span class="sxs-lookup"><span data-stu-id="6bf82-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="6bf82-317">**Wariant**  *v*</span><span class="sxs-lookup"><span data-stu-id="6bf82-317">**Variant**  *v*</span></span>|<span data-ttu-id="6bf82-318">**Obiekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-318">**Object**  *o*</span></span>|<span data-ttu-id="6bf82-319">Nigdy</span><span class="sxs-lookup"><span data-stu-id="6bf82-319">Never</span></span>|
|<span data-ttu-id="6bf82-320">**Obiekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-320">**Object**  *o*</span></span>|<span data-ttu-id="6bf82-321">**Wariant**  *v*</span><span class="sxs-lookup"><span data-stu-id="6bf82-321">**Variant**  *v*</span></span>|<span data-ttu-id="6bf82-322">Nigdy</span><span class="sxs-lookup"><span data-stu-id="6bf82-322">Never</span></span>|
|<span data-ttu-id="6bf82-323">**Typ Variant** ***\**** Funkcja *PV*     </span><span class="sxs-lookup"><span data-stu-id="6bf82-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="6bf82-324">**Obiekt ref**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="6bf82-325">Zawsze</span><span class="sxs-lookup"><span data-stu-id="6bf82-325">Always</span></span>|
|<span data-ttu-id="6bf82-326">**Obiekt ref**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-326">**Ref object**  *o*</span></span>|<span data-ttu-id="6bf82-327">**Typ Variant** ***\**** Funkcja *PV*     </span><span class="sxs-lookup"><span data-stu-id="6bf82-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="6bf82-328">Zawsze</span><span class="sxs-lookup"><span data-stu-id="6bf82-328">Always</span></span>|
|<span data-ttu-id="6bf82-329">**Wariant**  *v* **(VT_BYREF** *&#124;* **VT_ \* )**</span><span class="sxs-lookup"><span data-stu-id="6bf82-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="6bf82-330">**Obiekt**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-330">**Object**  *o*</span></span>|<span data-ttu-id="6bf82-331">Nigdy</span><span class="sxs-lookup"><span data-stu-id="6bf82-331">Never</span></span>|
|<span data-ttu-id="6bf82-332">**Wariant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="6bf82-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="6bf82-333">**Obiekt ref**  *o*</span><span class="sxs-lookup"><span data-stu-id="6bf82-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="6bf82-334">Tylko wtedy, gdy typ nie został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="6bf82-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6bf82-335">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bf82-335">See also</span></span>

- [<span data-ttu-id="6bf82-336">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="6bf82-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="6bf82-337">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="6bf82-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="6bf82-338">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6bf82-338">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="6bf82-339">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="6bf82-339">Copying and Pinning</span></span>](copying-and-pinning.md)
