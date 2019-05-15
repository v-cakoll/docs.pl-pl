---
title: Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: fcc13d82a2b27221c13f9277585c21196b47003d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591480"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)
W tym temacie opisano zadania i pojęć, które są skojarzone z rejestru.  
  
 Podczas programowania w języku Visual Basic, można uzyskać dostępu do rejestru za pomocą funkcji Visual Basic lub klasy rejestru programu .NET Framework. Informacje o hostach rejestru z systemu operacyjnego, a także informacji z aplikacji znajdującej się na komputerze. Praca z rejestru może naruszyć bezpieczeństwo, zezwalając na niewłaściwe dostęp do zasobów systemowych lub informacje chronione.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Utwórz klucz rejestru i określanie jego wartości](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Opisuje sposób używania `CreateSubKey` i `SetValue` metody `My.Computer.Registry` obiekt do tworzenia klucza rejestru i określanie jego wartości.  
  
 [Instrukcje: Odczytywanie wartości z klucza rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Opisuje sposób używania `GetValue` metody `My.Computer.Registry` obiektu można odczytać wartości z klucza rejestru.  
  
 [Instrukcje: Usuwanie klucza rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Opisuje sposób używania `DeleteSubKey` metody `My.Computer.Registry.CurrentUser` właściwości można usunąć klucza rejestru.  
  
 [Odczytywanie z rejestru i zapisywanie w nim za pomocą przestrzeni nazw Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Opisuje sposób używania `Registry` i `RegistryKey` klas .NET Framework w celu dostępu do rejestru.  
  
 [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 W tym artykule omówiono problemy dotyczące zabezpieczeń obejmujące rejestru.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Przedstawiono oraz wyjaśniono członkowie `My.Computer.Registry` obiektu.  
  
 <xref:Microsoft.Win32.Registry>  
 Przedstawia omówienie `Registry` klasy, wraz z linkami do poszczególnych kluczy i elementów członkowskich.
