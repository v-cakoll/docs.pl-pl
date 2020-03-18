---
title: Dostosowywanie organizowania parametrów — .NET
description: Dowiedz się, jak dostosować sposób organizowania parametrów przez firmę .NET do reprezentacji macierzystej.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400366"
---
# <a name="customizing-parameter-marshaling"></a>Dostosowywanie marshalingu parametrów

Gdy domyślne zachowanie organizowania parametrów środowiska uruchomieniowego .NET nie robi tego, co chcesz, można użyć atrybutu, <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> aby dostosować sposób organizowania parametrów.

## <a name="customizing-string-parameters"></a>Dostosowywanie parametrów ciągu

.NET ma wiele formatów dla organizowania ciągów. Metody te są podzielone na różne sekcje na ciągi w stylu C i formaty ciągów zorientowanych na system Windows.

### <a name="c-style-strings"></a>Ciągi w stylu C

Każdy z tych formatów przekazuje ciąg zakończony zerem do kodu macierzystego. Różnią się one kodowaniem natywnego ciągu.

| `System.Runtime.InteropServices.UnmanagedType`Wartość | Kodowanie |
|------------------------------------------------------|----------|
| Lpstr | ANSI |
| LPUTF8Str ( LPUTF8Str ) | UTF-8 |
| Lpwstr | UTF-16 |
| Płyta lptstr | UTF-16 |

Format <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> jest nieco inny. Podobnie `LPWStr`jak , organizuje ciąg do natywnego ciągu w stylu C zakodowanego w UTF-16. Jednak zarządzany podpis ma przekazać w ciągu przez odwołanie i pasujące podpis macierzysty przyjmuje ciąg według wartości. To rozróżnienie umożliwia użycie natywnego interfejsu API, który przyjmuje ciąg według wartości `StringBuilder`i modyfikuje go w miejscu bez konieczności używania . Zalecamy ręczne używanie tego formatu, ponieważ jest on podatny na pomylenie z niedopasowanymi podpisami macierzystymi i zarządzanymi.

### <a name="windows-centric-string-formats"></a>Formaty ciągów zorientowanych na system Windows

Podczas interakcji z interfejsami COM lub OLE prawdopodobnie okaże się, że `BSTR` funkcje macierzyste przyjmują ciągi jako argumenty. Można użyć <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> typu niezarządzanego do organizowania ciągu jako `BSTR`.

Jeśli wchodzisz w interakcję z interfejsami API WinRT, możesz użyć formatu <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> do zorganizowania ciągu jako `HSTRING`pliku .

## <a name="customizing-array-parameters"></a>Dostosowywanie parametrów tablicy

.NET udostępnia również wiele sposobów organizowania parametrów tablicy. Jeśli nazywasz interfejs API, który ma tablicy <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> w stylu C, należy użyć typu niezarządzanego. Jeśli wartości w tablicy wymagają niestandardowego organizowania, można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> pola na `[MarshalAs]` atrybut dla tego.

Jeśli używasz interfejsów API COM, prawdopodobnie będziesz musiał zorganizować `SAFEARRAY*`parametry tablicy jako s. W tym celu można <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> użyć typu niezarządzanego. Domyślny typ elementów `SAFEARRAY` można zobaczyć w tabeli na [dostosowywanie `object` pól](./customize-struct-marshaling.md#marshaling-systemobjects). Za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> pól <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> i można dostosować dokładny `SAFEARRAY`typ elementu .

## <a name="customizing-boolean-or-decimal-parameters"></a>Dostosowywanie parametrów logicznych lub dziesiętnych

Aby uzyskać informacje na temat organizowania parametrów logicznych lub dziesiętnych, zobacz [Dostosowywanie organizowania struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Dostosowywanie parametrów obiektu (tylko dla systemu Windows)

W systemie Windows środowisko uruchomieniowe .NET udostępnia wiele różnych sposobów organizowania parametrów obiektu do kodu macierzystego.

### <a name="marshaling-as-specific-com-interfaces"></a>Organizowanie jako specyficzne interfejsy COM

Jeśli interfejs API przyjmuje wskaźnik do obiektu COM, można `UnmanagedType` użyć dowolnego `object`z następujących formatów na typowane parametr, aby poinformować .NET do marszałka, jak te specyficzne interfejsy:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ponadto jeśli typ jest `[ComVisible(true)]` oznaczony lub jesteś organizowanie `object` typu, można <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> użyć formatu do organizowania obiektu jako otoki wywoływanej COM dla widoku COM typu.

### <a name="marshaling-to-a-variant"></a>Kierowanie do`VARIANT`

Jeśli natywny interfejs API `VARIANT`przyjmuje Win32 `object` , można użyć `VARIANT`formatu <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> parametru do organizowania obiektów jako s. Zobacz dokumentację [dostosowywania `object` pól](customize-struct-marshaling.md#marshaling-systemobjects) do mapowania `VARIANT` między typami i typami .NET.

### <a name="custom-marshalers"></a>Niestandardowi marshalerzy

Jeśli chcesz rzutować natywny interfejs COM do innego `UnmanagedType.CustomMarshaler` typu zarządzanego, można użyć formatu i <xref:System.Runtime.InteropServices.ICustomMarshaler> implementacji, aby zapewnić własny niestandardowy kod organizowania.
