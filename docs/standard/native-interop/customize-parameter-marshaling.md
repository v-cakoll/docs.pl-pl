---
title: Dostosowywanie organizowania parametrów — .NET
description: Dowiedz się, jak dostosować sposób organizowania parametrów przez platformę .NET do natywnej reprezentacji.
ms.date: 01/18/2019
ms.openlocfilehash: 1999cad057875f15b283421f87f485c2e5ca2306
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374315"
---
# <a name="customizing-parameter-marshaling"></a>Dostosowywanie marshalingu parametrów

Gdy domyślne zachowanie podczas organizowania parametrów środowiska uruchomieniowego platformy .NET nie wykonuje tego zadania, użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu, aby dostosować sposób organizowania parametrów.

## <a name="customizing-string-parameters"></a>Dostosowywanie parametrów ciągu

Platforma .NET ma różne formaty do organizowania ciągów. Te metody są podzielone na różne sekcje w ciągach w stylu C i w formatach ciągów skoncentrowanych na systemie Windows.

### <a name="c-style-strings"></a>Ciągi w stylu języka C

Każdy z tych formatów przekazuje ciąg zakończony znakiem null do kodu natywnego. Różnią się one od kodowania ciągu macierzystego.

| `System.Runtime.InteropServices.UnmanagedType`wartościami | Encoding |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType>Format jest nieco inny. Podobnie jak `LPWStr` , dzieli ciąg na natywny ciąg języka C zakodowany w UTF-16. Jednak sygnatura zarządzana przekazuje ciąg przez odwołanie, a pasujący podpis macierzysty przyjmuje ciąg przez wartość. To rozróżnienie umożliwia użycie natywnego interfejsu API, który przyjmuje ciąg przez wartość i modyfikuje go w miejscu bez konieczności używania `StringBuilder` . Zalecamy ręczne korzystanie z tego formatu, ponieważ jest podatny na pomyłkę w przypadku niezgodności z niezgodnymi z nimi i zarządzanymi podpisami.

### <a name="windows-centric-string-formats"></a>Formaty ciągu skoncentrowane na systemie Windows

W przypadku korzystania z interfejsów COM lub OLE prawdopodobnie okaże się, że funkcje natywne przyjmują ciągi jako `BSTR` argumenty. Możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> typu niezarządzanego, aby zorganizować ciąg jako `BSTR` .

Jeśli korzystasz z interfejsów API WinRT, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formatu do organizowania ciągu jako `HSTRING` .

## <a name="customizing-array-parameters"></a>Dostosowywanie parametrów tablicy

Platforma .NET udostępnia również wiele sposobów organizowania parametrów tablicowych. Jeśli wywołujesz interfejs API, który pobiera tablicę w stylu C, użyj <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> typu niezarządzanego. Jeśli wartości w tablicy wymagają dostosowanego kierowania, można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pola `[MarshalAs]` dla tego atrybutu.

Jeśli używasz interfejsów API modelu COM, prawdopodobnie trzeba będzie zorganizować parametry tablicy jako "s" `SAFEARRAY*` . W tym celu można użyć <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> typu niezarządzanego. Domyślny typ elementów `SAFEARRAY` można zobaczyć w tabeli na temat [dostosowywania `object` pól](./customize-struct-marshaling.md#marshal-systemobject). Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> pól i, <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> Aby dostosować dokładny typ elementu `SAFEARRAY` .

## <a name="customizing-boolean-or-decimal-parameters"></a>Dostosowywanie parametrów logicznych lub dziesiętnych

Aby uzyskać informacje na temat organizowania parametrów logicznych lub dziesiętnych, zobacz [Dostosowywanie organizowania struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Dostosowywanie parametrów obiektu (tylko system Windows)

W systemie Windows środowisko uruchomieniowe platformy .NET udostępnia wiele różnych sposobów organizowania parametrów obiektów w kodzie natywnym.

### <a name="marshaling-as-specific-com-interfaces"></a>Kierowanie jako określonych interfejsów COM

Jeśli interfejs API przyjmuje wskaźnik do obiektu COM, można użyć dowolnego z poniższych `UnmanagedType` formatów dla `object` parametru-type, aby poinformować platformę .NET, aby zorganizować jako te konkretne interfejsy:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ponadto, jeśli typ jest oznaczony `[ComVisible(true)]` lub przeniesiesz `object` Typ, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> formatu do skierowania obiektu jako otoki modelu COM dla widoku com typu.

### <a name="marshaling-to-a-variant"></a>Kierowanie do`VARIANT`

Jeśli natywny interfejs API przyjmuje `VARIANT` system Win32, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> formatu na `object` parametrze, aby zorganizować obiekty jako `VARIANT` s. Zapoznaj się z dokumentacją dotyczącą [dostosowywania `object` pól](customize-struct-marshaling.md#marshal-systemobject) dla mapowania między typami i `VARIANT` typami .NET.

### <a name="custom-marshalers"></a>Organizatorzy niestandardowi

Jeśli chcesz utworzyć projekt natywnego interfejsu COM w innym typie zarządzanym, możesz użyć `UnmanagedType.CustomMarshaler` formatu i implementacji, <xref:System.Runtime.InteropServices.ICustomMarshaler> Aby zapewnić własny, niestandardowy kod do organizowania.
