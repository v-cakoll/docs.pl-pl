---
title: Zabezpieczanie danych o stanie
description: Deklaruj dane stanu jako zmienne prywatne lub wewnętrzne, aby ograniczyć dostęp do nich. Takie dane są nadal dostępne za pomocą odbicia, serializacji i debugowania.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186823"
---
# <a name="securing-state-data"></a>Zabezpieczanie danych o stanie
Aplikacje, które obsługują poufne dane lub podejmują wszelkiego rodzaju decyzje dotyczące zabezpieczeń, muszą zachować te dane pod własną kontrolą i nie mogą zezwolić innemu potencjalnie złośliwemu kodowi na bezpośredni dostęp do danych. Najlepszym sposobem ochrony danych w pamięci jest zadeklarowanie danych jako zmiennych prywatnych lub wewnętrznych (z zakresem ograniczonym do tego samego zestawu). Jednak nawet te dane podlegają dostępowi, o którym powinieneś wiedzieć:  
  
- Za pomocą mechanizmów odbicia, wysoce zaufany kod, który może odwoływać się do obiektu można uzyskać i ustawić członków prywatnych.  
  
- Za pomocą serializacji, wysoce zaufany kod można skutecznie uzyskać i ustawić członków prywatnych, jeśli można uzyskać dostęp do odpowiednich danych w postaci serializowane obiektu.  
  
- W obszarze debugowania te dane mogą być odczytywane.  
  
 Upewnij się, że żadna z własnych metod lub właściwości nie udostępnia tych wartości przypadkowo.  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
