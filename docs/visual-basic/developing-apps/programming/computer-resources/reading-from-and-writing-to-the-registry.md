---
title: Odczytywanie z oraz zapisywanie do rejestru
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.Registry object, tasks
- registry [Visual Basic], writing to
- registry [Visual Basic], reading
ms.assetid: a13da106-185b-41d7-b23c-416da65e21e4
ms.openlocfilehash: 89db9ef9db4235c069d6239d32e4f8679fbabf0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349762"
---
# <a name="reading-from-and-writing-to-the-registry-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru (Visual Basic)

W tym temacie opisano tematy dotyczące zadań i pojęć, które są skojarzone z rejestrem.  
  
 Podczas programowania w Visual Basic można wybrać dostęp do rejestru za pomocą funkcji udostępnianych przez Visual Basic lub klasy rejestru .NET Framework. Rejestr zawiera informacje z systemu operacyjnego oraz informacje z aplikacji hostowanych na komputerze. Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji.  
  
## <a name="in-this-section"></a>W tej sekcji  

 [Instrukcje: tworzenie klucza rejestru i określanie jego wartości](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-create-a-registry-key-and-set-its-value.md)  
 Opisuje sposób używania metod `CreateSubKey` i `SetValue` obiektu `My.Computer.Registry` do tworzenia klucza rejestru i ustawiania jego wartości.  
  
 [Instrukcje: odczytywanie wartości z klucza rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-read-a-value-from-a-registry-key.md)  
 Opisuje sposób użycia metody `GetValue` obiektu `My.Computer.Registry` do odczytywania wartości z klucza rejestru.  
  
 [Instrukcje: usuwanie klucza rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-delete-a-registry-key.md)  
 Opisuje sposób używania metody `DeleteSubKey` właściwości `My.Computer.Registry.CurrentUser` do usuwania klucza rejestru.  
  
 [Odczytywanie z rejestru i zapisywanie w nim za pomocą przestrzeni nazw Microsoft.Win32](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace.md)  
 Opisuje sposób używania klas `Registry` i `RegistryKey` .NET Framework w celu uzyskania dostępu do rejestru.  
  
 [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 Omawia problemy z zabezpieczeniami związane z rejestrem.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 Wyświetla listę i objaśnia elementy członkowskie obiektu `My.Computer.Registry`.  
  
 <xref:Microsoft.Win32.Registry>  
 Przedstawia przegląd klasy `Registry` wraz z łączami do poszczególnych kluczy i członków.
