---
title: Dostosowywanie organizowania parametrów — .NET
description: Dowiedz się, jak dostosować sposób organizowania parametrów przez platformę .NET do natywnej reprezentacji.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400366"
---
# <a name="customizing-parameter-marshaling"></a>Dostosowywanie marshalingu parametrów

Gdy domyślne zachowanie podczas organizowania parametrów środowiska uruchomieniowego platformy .NET nie wykonuje tego zadania, użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu, aby dostosować sposób organizowania parametrów.

## <a name="customizing-string-parameters"></a>Dostosowywanie parametrów ciągu

Platforma .NET ma różne formaty do organizowania ciągów. Te metody są podzielone na różne sekcje w ciągach w stylu C i w formatach ciągów skoncentrowanych na systemie Windows.

### <a name="c-style-strings"></a>Ciągi w stylu języka C

Każdy z tych formatów przekazuje ciąg zakończony znakiem null do kodu natywnego. Różnią się one od kodowania ciągu macierzystego.

| `System.Runtime.InteropServices.UnmanagedType`wartościami | Kodowanie |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Format jest nieco inny. Podobnie `LPWStr`jak, dzieli ciąg na natywny ciąg języka C zakodowany w UTF-16. Jednak sygnatura zarządzana przekazuje ciąg przez odwołanie, a pasujący podpis macierzysty przyjmuje ciąg przez wartość. To rozróżnienie umożliwia użycie natywnego interfejsu API, który przyjmuje ciąg przez wartość i modyfikuje go w miejscu bez konieczności używania `StringBuilder`. Zalecamy ręczne korzystanie z tego formatu, ponieważ jest podatny na pomyłkę w przypadku niezgodności z niezgodnymi z nimi i zarządzanymi podpisami.

### <a name="windows-centric-string-formats"></a>Formaty ciągu skoncentrowane na systemie Windows

W przypadku korzystania z interfejsów COM lub OLE prawdopodobnie okaże się, że funkcje natywne przyjmują ciągi jako `BSTR` argumenty. Możesz użyć typu <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> niezarządzanego, aby zorganizować ciąg jako `BSTR`.

Jeśli korzystasz z interfejsów API WinRT, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> formatu do organizowania ciągu jako. `HSTRING`

## <a name="customizing-array-parameters"></a>Dostosowywanie parametrów tablicy

Platforma .NET udostępnia również wiele sposobów organizowania parametrów tablicowych. Jeśli wywołujesz interfejs API, który pobiera tablicę w stylu C, użyj typu <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> niezarządzanego. Jeśli wartości w tablicy wymagają dostosowanego kierowania, można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pola dla tego `[MarshalAs]` atrybutu.

Jeśli używasz interfejsów API modelu COM, prawdopodobnie trzeba będzie zorganizować parametry tablicy jako `SAFEARRAY*`"s". W tym celu można użyć typu <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> niezarządzanego. Domyślny typ elementów `SAFEARRAY` można zobaczyć w tabeli na temat [dostosowywania `object` pól](./customize-struct-marshaling.md#marshaling-systemobjects). Możesz użyć pól <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> , aby dostosować dokładny typ elementu. `SAFEARRAY`

## <a name="customizing-boolean-or-decimal-parameters"></a>Dostosowywanie parametrów logicznych lub dziesiętnych

Aby uzyskać informacje na temat organizowania parametrów logicznych lub dziesiętnych, zobacz [Dostosowywanie organizowania struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Dostosowywanie parametrów obiektu (tylko system Windows)

W systemie Windows środowisko uruchomieniowe platformy .NET udostępnia wiele różnych sposobów organizowania parametrów obiektów w kodzie natywnym.

### <a name="marshaling-as-specific-com-interfaces"></a>Kierowanie jako określonych interfejsów COM

Jeśli interfejs API przyjmuje wskaźnik do obiektu COM, można użyć dowolnego z poniższych `UnmanagedType` formatów dla parametru `object`-Type, aby poinformować platformę .NET, aby zorganizować jako te konkretne interfejsy:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ponadto, jeśli typ jest oznaczony `[ComVisible(true)]` lub przeniesiesz `object` typ, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> formatu do skierowania obiektu jako otoki modelu COM dla widoku com typu.

### <a name="marshaling-to-a-variant"></a>Kierowanie do`VARIANT`

Jeśli natywny interfejs API przyjmuje system `VARIANT`Win32, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> formatu na `object` parametrze, aby zorganizować obiekty jako `VARIANT`s. Zapoznaj się z dokumentacją dotyczącą [dostosowywania `object` pól](customize-struct-marshaling.md#marshaling-systemobjects) dla mapowania między typami `VARIANT` i typami .NET.

### <a name="custom-marshalers"></a>Organizatorzy niestandardowi

Jeśli chcesz utworzyć projekt natywnego interfejsu COM w innym typie zarządzanym, możesz użyć `UnmanagedType.CustomMarshaler` formatu i implementacji, aby zapewnić własny, <xref:System.Runtime.InteropServices.ICustomMarshaler> niestandardowy kod do organizowania.
