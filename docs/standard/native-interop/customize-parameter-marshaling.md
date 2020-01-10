---
title: Dostosowywanie organizowania parametrów — .NET
description: Dowiedz się, jak dostosować sposób organizowania parametrów przez platformę .NET do natywnej reprezentacji.
ms.date: 01/18/2019
ms.openlocfilehash: 36fb8c105a8836d77b862095a616de3ba641073c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706364"
---
# <a name="customizing-parameter-marshaling"></a>Dostosowywanie marshalingu parametrów

Gdy domyślne zachowanie podczas organizowania parametrów środowiska uruchomieniowego platformy .NET nie wykonuje tego zadania, można użyć atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>, aby dostosować sposób organizowania parametrów.

## <a name="customizing-string-parameters"></a>Dostosowywanie parametrów ciągu

Platforma .NET ma różne formaty do organizowania ciągów. Te metody są podzielone na różne sekcje w ciągach w stylu C i w formatach ciągów skoncentrowanych na systemie Windows.

### <a name="c-style-strings"></a>Ciągi w stylu języka C

Każdy z tych formatów przekazuje ciąg zakończony znakiem null do kodu natywnego. Różnią się one od kodowania ciągu macierzystego.

| wartość `System.Runtime.InteropServices.UnmanagedType` | Kodowanie |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

Format <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> jest nieco inny. Podobnie jak `LPWStr`, organizowane jest ciąg do natywnego ciągu w stylu C zakodowanego w UTF-16. Jednak sygnatura zarządzana przekazuje ciąg przez odwołanie, a pasujący podpis macierzysty przyjmuje ciąg przez wartość. To rozróżnienie umożliwia użycie natywnego interfejsu API, który przyjmuje ciąg przez wartość i modyfikuje go w miejscu bez konieczności używania `StringBuilder`. Zalecamy ręczne korzystanie z tego formatu, ponieważ jest podatny na pomyłkę w przypadku niezgodności z niezgodnymi z nimi i zarządzanymi podpisami.

### <a name="windows-centric-string-formats"></a>Formaty ciągu skoncentrowane na systemie Windows

W przypadku korzystania z interfejsów COM lub OLE prawdopodobnie okaże się, że funkcje natywne przyjmują ciągi jako argumenty `BSTR`. Możesz użyć niezarządzanego typu <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, aby zorganizować ciąg jako `BSTR`.

Jeśli korzystasz z interfejsów API WinRT, możesz użyć formatu <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, aby zorganizować ciąg jako `HSTRING`.

## <a name="customizing-array-parameters"></a>Dostosowywanie parametrów tablicy

Platforma .NET udostępnia również wiele sposobów organizowania parametrów tablicowych. Jeśli wywołujesz interfejs API, który pobiera tablicę w stylu C, użyj <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> typu niezarządzanego. Jeśli wartości w tablicy wymagają dostosowanego kierowania, można użyć pola <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> w atrybucie `[MarshalAs]` dla tego elementu.

Jeśli używasz interfejsów API modelu COM, prawdopodobnie trzeba będzie zorganizować parametry tablicy jako `SAFEARRAY*`s. W tym celu można użyć typu niezarządzanego <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>. Domyślny typ elementów `SAFEARRAY` można zobaczyć w tabeli na temat [dostosowywania pól `object`](./customize-struct-marshaling.md#marshaling-systemobjects). Można użyć pól <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> do dostosowania dokładnego typu elementu `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Dostosowywanie parametrów logicznych lub dziesiętnych

Aby uzyskać informacje na temat organizowania parametrów logicznych lub dziesiętnych, zobacz [Dostosowywanie organizowania struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Dostosowywanie parametrów obiektu (tylko system Windows)

W systemie Windows środowisko uruchomieniowe platformy .NET udostępnia wiele różnych sposobów organizowania parametrów obiektów w kodzie natywnym.

### <a name="marshaling-as-specific-com-interfaces"></a>Kierowanie jako określonych interfejsów COM

Jeśli Twój interfejs API przyjmuje wskaźnik do obiektu COM, można użyć dowolnego z poniższych `UnmanagedType` formatów na parametrze typu `object`, aby poinformować platformę .NET, aby mogli zorganizować się jako te określone interfejsy:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ponadto, jeśli typ jest oznaczony `[ComVisible(true)]` lub organizowane jest typ `object`, można użyć formatu <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> do organizowania obiektu jako otoki COM dla widoku COM dla danego typu.

### <a name="marshaling-to-a-variant"></a>Kierowanie do `VARIANT`

Jeśli natywny interfejs API przyjmuje `VARIANT`Win32, można użyć formatu <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> na `object` parametr, aby zorganizować obiekty jako `VARIANT`s. Zapoznaj się z dokumentacją dotyczącą [dostosowywania `object` pól](customize-struct-marshaling.md#marshaling-systemobjects) , aby uzyskać mapowanie między typami .net a typami `VARIANT`.

### <a name="custom-marshalers"></a>Organizatorzy niestandardowi

Jeśli chcesz utworzyć projekt natywnego interfejsu COM w innym typie zarządzanym, możesz użyć formatu `UnmanagedType.CustomMarshaler` i implementacji <xref:System.Runtime.InteropServices.ICustomMarshaler>, aby zapewnić własny, niestandardowy kod do organizowania.
