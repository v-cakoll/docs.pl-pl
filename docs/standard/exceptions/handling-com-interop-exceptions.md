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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708935"
---
# <a name="handling-com-interop-exceptions"></a>Obsługa wyjątków międzyoperacyjności COM
Kod zarządzany i niezarządzany może współdziałać ze sobą w celu obsługi wyjątków. Jeśli metoda zgłasza wyjątek w kodzie zarządzanym, środowisko uruchomieniowe języka wspólnego może przekazać wynik HRESULT do obiektu COM. Jeśli metoda zakończy się niepowodzeniem w kodzie niezarządzanym przez zwrócenie błędu HRESULT, środowisko uruchomieniowe zgłasza wyjątek, który może zostać przechwycony przez kod zarządzany.  
  
 Środowisko uruchomieniowe automatycznie mapuje wynik HRESULT z międzyoperacyjności modelu COM do bardziej szczegółowych wyjątków. Na przykład E_ACCESSDENIED zostanie <xref:System.UnauthorizedAccessException>, E_OUTOFMEMORY <xref:System.OutOfMemoryException>i tak dalej.  
  
 Jeśli HRESULT jest wynikiem niestandardowym lub jeśli jest nieznany dla środowiska uruchomieniowego, środowisko uruchomieniowe przekazuje do klienta ogólne <xref:System.Runtime.InteropServices.COMException>. Właściwość **ErrorCode** elementu **COMEXCEPTION** zawiera wartość HRESULT.  
  
## <a name="working-with-ierrorinfo"></a>Praca z IErrorInfo  
 Po przekazaniu błędu z modelu COM do kodu zarządzanego środowisko uruchomieniowe wypełnia obiekt wyjątku informacjami o błędzie. Obiekty COM obsługujące IErrorInfo i zwracają wartości HRESULT zawierają te informacje do wyjątków kodu zarządzanego. Na przykład środowisko uruchomieniowe mapuje opis z błędu COM na Właściwość <xref:System.Exception.Message%2A> wyjątku. Jeśli HRESULT nie zawiera żadnych dodatkowych informacji o błędzie, środowisko uruchomieniowe wypełnia wiele właściwości wyjątku z wartościami domyślnymi.  
  
 Jeśli metoda zakończy się niepowodzeniem w kodzie niezarządzanym, można przekazywać wyjątek do segmentu kodu zarządzanego. Temat [HResults i Exceptions](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md) zawiera tabelę przedstawiającą sposób, w jaki HRESULT są mapowane na obiekty wyjątków czasu wykonywania.  

## <a name="see-also"></a>Zobacz także

- [Wyjątki](index.md)
