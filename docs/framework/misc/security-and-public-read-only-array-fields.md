---
title: "Bezpieczeństwo i publiczne pola tablicy tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d054d3a5a4e10b8efcc3292f3a18ea37f9b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-public-read-only-array-fields"></a>Bezpieczeństwo i publiczne pola tablicy tylko do odczytu
Nigdy nie używaj tylko do odczytu publiczne pola tablicy z bibliotek zarządzanych do definiowania zachowania granic lub zabezpieczeń aplikacji, ponieważ mogą być modyfikowane tylko do odczytu publiczne pola tablicy.  
  
## <a name="remarks"></a>Uwagi  
 Niektóre klasy framework .NET zawierają tylko do odczytu pola publiczne, zawierających parametry specyficzne dla platformy granic.  Na przykład <xref:System.IO.Path.InvalidPathChars> pole jest tablicę, która opisuje znaki, które nie są dozwolone w ciągu ścieżki pliku.  Wiele podobnych pól znajdują się w programie .NET Framework.  
  
 Wartości pola publiczne tylko do odczytu, takich jak <xref:System.IO.Path.InvalidPathChars> można zmodyfikować przez kod lub kod, który udostępnia swój kod domeny aplikacji.  Nie należy używać tylko do odczytu publiczne pola tablicy takie Definiowanie zachowania granic aplikacji.  Jeśli to zrobisz, złośliwy kod może zmiany definicji granic i używać kodu w nieoczekiwany sposób.  
  
 W wersji 2.0 lub nowszej programu .NET Framework należy użyć metody, które zwracają nowe tablicy zamiast publiczne pola tablicy.  Na przykład zamiast <xref:System.IO.Path.InvalidPathChars> pola, należy użyć <xref:System.IO.Path.GetInvalidPathChars%2A> metody.  
  
 Należy pamiętać, że typy .NET Framework nie pola publiczne wewnętrznie określenie typów granic.  Zamiast tego programu .NET Framework używa oddzielnych pól prywatnych.  Zmiana wartości te pola publiczne nie zmienia zachowanie typów .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
