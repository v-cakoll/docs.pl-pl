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
ms.openlocfilehash: 9f4429d50f6b7646cb75fad44957a98812282928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-com-interop-exceptions"></a>Obsługa wyjątków międzyoperacyjności COM
Zarządzanego i kodu niezarządzanego mogą współdziałać ze sobą do obsługi wyjątków. Jeśli metoda zgłosi wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego można przekazać HRESULT do obiektów COM. W przypadku niepowodzenia metody za pomocą kodu niezarządzanego zwracając błąd HRESULT środowiska uruchomieniowego zgłasza wyjątek, który może być przechwycony przez kod zarządzany.  
  
 Środowisko uruchomieniowe mapuje automatycznie HRESULT z międzyoperacyjności z modelem COM na bardziej szczegółowe wyjątki. Na przykład, staje się E_ACCESSDENIED <xref:System.UnauthorizedAccessException>, staje się E_OUTOFMEMORY <xref:System.OutOfMemoryException>i tak dalej.  
  
 Jeśli HRESULT znajduje się wynik niestandardowych lub jeśli jest on nieznany do środowiska wykonawczego, środowisko uruchomieniowe przekazuje ogólnego <xref:System.Runtime.InteropServices.COMException> do klienta. **ErrorCode** właściwość **COMException** zawiera wartość HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Praca z IErrorInfo  
 Po upływie błąd z modelu COM do kodu zarządzanego środowiska wykonawczego wypełnia obiekt wyjątku z informacje o błędzie. Obiekty COM, które obsługują IErrorInfo i zwrócić wyników HRESULT Przekaż te informacje do wyjątków kodu zarządzanego. Na przykład środowiska uruchomieniowego mapuje opis błędu COM z wyjątkiem <xref:System.Exception.Message%2A> właściwości. Jeśli wynik HRESULT udostępnia nie dodatkowe informacje o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.  
  
 Jeśli metoda nie powiedzie się za pomocą kodu niezarządzanego, wyjątek mogą być przekazywane do segmentu kodu zarządzanego. Temat [wyników HRESULT i wyjątków](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą jak mapowanie wyników HRESULT do obiektów wyjątek czasu wykonywania.  

## <a name="see-also"></a>Zobacz też
[Wyjątki](index.md) 
