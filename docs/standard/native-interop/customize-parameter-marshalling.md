---
title: Dostosowywanie parametrów kierowania — .NET
description: Dowiedz się, jak dostosować, jak .NET kieruje parametry do natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 7821da546e0ed0ab5fa97d00a638aa5cc1a3089c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973592"
---
# <a name="customizing-parameter-marshalling"></a>Dostosowywanie parametrów kierowania

Podczas zachowanie kierujące parametr domyślne środowisko uruchomieniowe platformy .NET nie robi, co chcesz zrobić, użyj można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu, aby dostosować, jak parametry są przekazywane.

## <a name="customizing-string-parameters"></a>Dostosowywanie parametrów

.NET zawiera różne formaty ciągów zarządzany. Te metody są dzielone na różne sekcje na ciągi stylu C i skoncentrowane na Windows formaty ciągu.

### <a name="c-style-strings"></a>Ciągi stylu C

Każda z tych formatów przekazuje ciąg zakończony wartością null do kodu natywnego. Różnią się one kodowanie ciągu natywnych.

| `System.Runtime.InteropServices.UnmanagedType` Wartość | Kodowanie |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 | 
| LPWStr | UTF-16 |

<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> Format jest nieco inny. Podobnie jak `LPWStr`, kieruje go ciągu na ciąg stylu C natywnych zakodowane w formacie UTF-16. Jednak ma zarządzanego podpisu, należy przekazać w ciągu przez odwołanie i pasujący podpis natywnych przenosi ciąg przez wartość. Wykonywania tego rozróżnienia pozwala na używanie natywnych interfejsów API, przyjmuje ciąg przez wartość, która modyfikuje go w miejscu bez konieczności używania `StringBuilder`. Zaleca się ręcznie przy użyciu tego formatu, ponieważ jest podatny na dezorientację z niezgodną sygnaturami natywne i zarządzane.

### <a name="windows-centric-string-formats"></a>Formaty ciągu skoncentrowane na Windows

Podczas interakcji z interfejsem COM lub OLE, prawdopodobnie okaże, funkcje natywne pobierają ciągi jako `BSTR` argumentów. Możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> niezarządzany typ, aby kierować ciąg w kodowaniu `BSTR`.

Jeśli masz interakcje interfejsów API WinRT, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> format, aby kierować ciąg w kodowaniu `HSTRING`.

## <a name="customizing-array-parameters"></a>Dostosowywanie tablicy parametrów

.NET zawiera również wiele sposobów, aby marshal tablicy parametrów. Jeśli w przypadku wywoływania interfejsu API, który przyjmuje tablicy stylu C, należy użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> niezarządzanego typu. Jeśli kierowania dostosowanych wartości w tablicy, możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> na `[MarshalAs]` atrybutu dla tego.

Jeśli używasz interfejsów API modelu COM, prawdopodobnie będziesz mieć do organizowania parametry tablicy jako `SAFEARRAY*`s. Aby to zrobić, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> niezarządzanego typu. Domyślny typ elementów `SAFEARRAY` będą widoczne w tabeli na [dostosowywanie `object` pola](./customize-struct-marshalling.md#marshalling-systemobjects). Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> typu pola, aby dostosować element dokładnie `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Dostosowywanie parametrów logiczną lub dziesiętną

Instrukcje dotyczące kierowania logiczną lub dziesiętną parametrów, zobacz [Dostosowywanie struktury kierowania](customize-struct-marshalling.md).

## <a name="customizing-object-parameters-windows-only"></a>Dostosowywanie parametrów obiektu (tylko Windows)

W Windows środowisko uruchomieniowe platformy .NET udostępnia wiele różnych sposobów, aby zorganizować parametrów obiektu do kodu macierzystego.

### <a name="marshalling-as-specific-com-interfaces"></a>Kierowania jako określonych interfejsów COM

Jeśli Twój interfejs API pobiera wskaźnik do obiektu COM, można użyć dowolnej z następujących `UnmanagedType` formatuje na `object`-wpisane parametru, aby poinformować .NET do organizowania jako tych określonych interfejsów:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Ponadto jeśli Twój typ jest oznaczony `[ComVisible(true)]` lub w przypadku kierowania `object` typu, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> format marshalingu obiektu jako wywołalne opakowanie COM dla widoku COM tego typu.

### <a name="marshalling-to-a-variant"></a>Kierowania do `VARIANT`

Jeśli natywnego interfejsu API systemu Win32 `VARIANT`, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> sformatować w swojej `object` parametru do organizowania obiektów jako `VARIANT`s. Zajrzyj do dokumentacji na [dostosowywanie `object` pola](customize-struct-marshalling.md#marshalling-systemobjects) mapowania między typami .NET i `VARIANT` typów.

### <a name="custom-marshalers"></a>Niestandardowi

Jeśli chcesz wyświetlić macierzysty interfejs COM do innego typu zarządzanego, możesz użyć `UnmanagedType.CustomMarshaler` format i implementację <xref:System.Runtime.InteropServices.ICustomMarshaler> zapewnienie własny niestandardowy kod zarządzany.
