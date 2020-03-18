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
ms.openlocfilehash: 17cd739ac40b43bdd4a93b83a4ab9d0d92400e2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708935"
---
# <a name="handling-com-interop-exceptions"></a>Obsługa wyjątków międzyoperacyjności COM
Kod zarządzany i niezarządzany może współpracować w celu obsługi wyjątków. Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, czas wykonywania języka wspólnego może przekazać HRESULT do obiektu COM. Jeśli metoda nie powiedzie się w kodzie niezarządzanym przez zwrócenie błędu HRESULT, czas wykonywania zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.  
  
 Czas wykonywania automatycznie mapuje HRESULT z com interop do bardziej szczegółowych wyjątków. Na przykład, E_ACCESSDENIED <xref:System.UnauthorizedAccessException>staje się <xref:System.OutOfMemoryException>, E_OUTOFMEMORY staje się , i tak dalej.  
  
 Jeśli Wynik HRESULT jest wynikiem niestandardowym lub jeśli nie jest znany <xref:System.Runtime.InteropServices.COMException> do czasu wykonywania, czas wykonywania przekazuje ogólny do klienta. **Właściwość ErrorCode** **comexception** zawiera wartość HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Praca z IErrorInfo  
 Gdy błąd jest przekazywany z COM do kodu zarządzanego, czas wykonywania wypełnia obiekt wyjątku z informacjami o błędzie. Obiekty COM, które obsługują IErrorInfo i zwracają HRESULTS podać te informacje do wyjątków kodu zarządzanego. Na przykład czas wykonywania mapuje opis z błędu <xref:System.Exception.Message%2A> COM do właściwości wyjątku. Jeśli HRESULT nie zawiera żadnych dodatkowych informacji o błędzie, czas wykonywania wypełnia wiele właściwości wyjątku wartościami domyślnymi.  
  
 Jeśli metoda nie powiedzie się w kodzie niezarządzanym, wyjątek można przekazać do segmentu kodu zarządzanego. Temat [HRESULTS i wyjątki](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę pokazującą, jak Mapa HRESULTS do obiektów wyjątków w czasie wykonywania.  

## <a name="see-also"></a>Zobacz też

- [Wyjątki](index.md)
