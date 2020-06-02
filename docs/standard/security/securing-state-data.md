---
title: Zabezpieczanie danych o stanie
description: Zadeklaruj dane stanu jako zmienne prywatne lub wewnętrzne, aby ograniczyć dostęp do niego. Dostęp do tych danych można nadal uzyskać poprzez odbicie, serializację i debugowanie.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: b7fcb520fe6fa28cc098c4e1cbb56ce7da759c11
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291048"
---
# <a name="securing-state-data"></a>Zabezpieczanie danych o stanie
Aplikacje, które obsługują dane poufne lub podejmują jakiekolwiek decyzje dotyczące zabezpieczeń, muszą zachować te dane w ramach własnych kontroli i nie mogą być bezpośrednio dostępne w innym potencjalnie złośliwym kodzie. Najlepszym sposobem ochrony danych w pamięci jest zadeklarowanie danych jako prywatnych lub wewnętrznych (z zakresem ograniczonym do tego samego zestawu). Jednak nawet te dane podlegają dostępowi, należy pamiętać o:  
  
- Korzystanie z mechanizmów odbicia, wysoce zaufany kod, który może odwoływać się do obiektu, może pobierać i ustawiać prywatnych członków.  
  
- Przy użyciu serializacji wysoce zaufany kod może efektywnie uzyskać i ustawić prywatne składowe, jeśli ma dostęp do odpowiednich danych w serializowanej formie obiektu.  
  
- W obszarze Debugowanie można odczytać te dane.  
  
 Upewnij się, że żadna z własnych metod lub właściwości nie ujawnia tych wartości przypadkowo.  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](secure-coding-guidelines.md)
