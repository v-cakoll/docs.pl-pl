---
title: Obsługa wyjątków międzyoperacyjności COM
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a17752257589ea4ee4d9e58182d4448f02f6460
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46568624"
---
# <a name="handling-com-interop-exceptions"></a>Obsługa wyjątków międzyoperacyjności COM
Zarządzanego i niezarządzanego kodu mogą współpracować ze sobą, aby obsłużyć wyjątki. Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego może przekazywać wartość HRESULT do obiektu COM. Jeśli metoda nie powiedzie się w niezarządzanym kodzie, zwracając błąd HRESULT, środowisko wykonawcze zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.  
  
 Środowisko wykonawcze automatycznie mapuje wynik HRESULT COM interop bardziej szczegółowe wyjątki. Na przykład staje się E_ACCESSDENIED <xref:System.UnauthorizedAccessException>, staje się E_OUTOFMEMORY <xref:System.OutOfMemoryException>i tak dalej.  
  
 Jeśli HRESULT znajduje się wynik niestandardowych lub jeśli jest nieznany do środowiska uruchomieniowego, środowisko uruchomieniowe przekazuje ogólnego <xref:System.Runtime.InteropServices.COMException> do klienta. **ErrorCode** właściwość **COMException** zawiera wartość HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Praca z IErrorInfo  
 Gdy błąd jest przekazywany z modelu COM z kodem zarządzanym, środowisko uruchomieniowe wypełnia obiekt wyjątku przy użyciu informacji o błędzie. Obiekty COM, które obsługują IErrorInfo i zwracać wartości HRESULT przekazać tę informację do wyjątków w kodzie zarządzanym. Na przykład, środowisko uruchomieniowe mapuje opis błędu modelu COM, z wyjątkiem <xref:System.Exception.Message%2A> właściwości. Jeśli wynik HRESULT udostępniane nie dodatkowe informacje o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.  
  
 Jeśli metoda nie powiedzie się w niezarządzanym kodzie, wyjątek może być przekazywany do segmentu kodu zarządzanego. Temat [wyników HRESULT i wyjątków](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą sposób mapowania wartości HRESULT do obiektów wyjątków czasu wykonywania.  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
