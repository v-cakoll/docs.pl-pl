---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
ms.openlocfilehash: 2df4acc0606e4fe8fccee4a8acc6ab744dcbbb71
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452711"
---
# <a name="security-and-public-read-only-array-fields"></a>Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
Nie używaj pól tablicy publicznej tylko do odczytu z bibliotek zarządzanych, aby zdefiniować zachowanie granic lub zabezpieczenia aplikacji, ponieważ można modyfikować pola tablicy publicznej tylko do odczytu.  
  
## <a name="remarks"></a>Uwagi  

Niektóre klasy .NET zawierają pola publiczne tylko do odczytu, które zawierają parametry graniczne specyficzne dla platformy. Na przykład pole <xref:System.IO.Path.InvalidPathChars> jest tablicą opisującą znaki, które nie są dozwolone w ciągu ścieżki do pliku. W środowisku .NET są obecne wiele podobnych pól.  
  
 Wartości publicznych pól tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars>, mogą być modyfikowane przez kod lub kod, który współużytkuje domenę aplikacji Twojego kodu.  Nie należy używać pól tablic publicznych tylko do odczytu, takich jak to, aby zdefiniować zachowanie granic aplikacji.  Jeśli to zrobisz, złośliwy kod może zmienić definicje granic i użyć kodu w nieoczekiwany sposób.  
  
 W wersji 2,0 i nowszych .NET Framework należy używać metod, które zwracają nową tablicę zamiast używać publicznych pól tablic.  Na przykład zamiast używać pola <xref:System.IO.Path.InvalidPathChars>, należy użyć metody <xref:System.IO.Path.GetInvalidPathChars%2A>.  
  
 Należy zauważyć, że typy .NET Framework nie używają publicznych pól do wewnętrznego definiowania typów granic.  Zamiast tego .NET Framework używa oddzielnych pól prywatnych.  Zmiana wartości tych pól publicznych nie powoduje zmiany zachowania typów .NET Framework.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
