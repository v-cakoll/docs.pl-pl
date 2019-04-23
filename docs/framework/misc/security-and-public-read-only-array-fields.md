---
title: Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19b5ad73150697c1442056642a1b11d504ecc426
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113779"
---
# <a name="security-and-public-read-only-array-fields"></a>Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
Nigdy nie używaj tylko do odczytu publiczne pola tablicy z zarządzanych bibliotek do definiowania zachowania granic lub bezpieczeństwem Twoich aplikacji, ponieważ tylko do odczytu publiczne pola tablicy można modyfikować.  
  
## <a name="remarks"></a>Uwagi  
 Niektóre klasy framework .NET zawierają tylko do odczytu publicznych pola, które zawierają parametry specyficzne dla platformy granic.  Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablica, która opisuje znaki, które nie są dozwolone w ciąg ścieżki pliku.  Wiele podobnych pól znajdują się w całym programie .NET Framework.  
  
 Wartości pola publiczne tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> można zmodyfikować przez kod lub kod, który udostępnia swój kod domeny aplikacji.  Nie należy używać tylko do odczytu publiczne pola tablicy następująco do określania zachowania granic aplikacji.  Jeśli to zrobisz, złośliwy kod może zmiany definicji granic i użyciu kodu w nieoczekiwany sposób.  
  
 W wersji 2.0 i nowszej programu .NET Framework należy użyć metody, które zwracają nową tablicę zamiast publiczne pola tablicy.  Na przykład, zamiast <xref:System.IO.Path.InvalidPathChars> pola, należy użyć <xref:System.IO.Path.GetInvalidPathChars%2A> metody.  
  
 Należy pamiętać, że typów programu .NET Framework nie należy używać pola publiczne do definiowania typów granic wewnętrznie.  Zamiast programu .NET Framework używa oddzielnych pól prywatnych.  Zmiana wartości te pola publiczne nie zmienia zachowanie typów programu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
