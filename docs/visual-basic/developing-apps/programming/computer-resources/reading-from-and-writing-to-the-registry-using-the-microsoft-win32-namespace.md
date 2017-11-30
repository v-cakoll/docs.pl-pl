---
title: "Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 462cc5c3854035cfc04c7c5df6905c2cfbd486ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)
Mimo że `My.Computer.Registry` powinno obejmować potrzeb podstawowe, gdy Programowanie w odniesieniu do rejestru, można również użyć <xref:Microsoft.Win32.Registry> i <xref:Microsoft.Win32.RegistryKey> klas w <xref:Microsoft.Win32> przestrzeń nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Klucze rejestru klasy  
 <xref:Microsoft.Win32.Registry> Klasa zapewnia kluczy rejestru podstawowej, które mogą być używane do dostępu podklucze i ich wartości. Podstawowy samych kluczy są tylko do odczytu. Poniższej tabeli wymieniono i opisano klucze siedmiu udostępnianych przez <xref:Microsoft.Win32.Registry> klasy.  
  
|**Klucz**|**Opis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Określa typy dokumentów i właściwości skojarzone z tych typów.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Zawiera informacje o konfiguracji sprzętu, który nie jest specyficzne dla użytkownika.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Zawiera informacje o bieżącym preferencje użytkownika, takie jak zmiennych środowiskowych.|  
|<xref:Microsoft.Win32.Registry.DynData>|Zawiera dane rejestru dynamicznych, takie jak używany przez sterowniki urządzeń wirtualnych.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Zawiera pięć podkluczy (sprzętu, SAM zabezpieczeń, oprogramowania i systemu) zawierających dane konfiguracji na komputerze lokalnym.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Zawiera informacje o wydajności dla składników oprogramowania.|  
|<xref:Microsoft.Win32.Registry.Users>|Zawiera informacje o domyślnych preferencji użytkownika.|  
  
> [!IMPORTANT]
>  Jest bardziej bezpieczne można zapisać danych do bieżącego użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>) niż do komputera lokalnego (<xref:Microsoft.Win32.Registry.LocalMachine>). Warunek, który jest zwykle nazywany "tureckie" występuje podczas tworzenia klucza wcześniej została utworzona przez inny proces potencjalnie szkodliwymi. Aby temu zapobiec, należy użyć metody, takie jak <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, która zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
## <a name="reading-a-value-from-the-registry"></a>Odczytywanie wartości z rejestru  
 Poniższy kod przedstawia sposób odczytywania ciąg z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 Poniższy kod odczytuje zwiększa, a następnie zapisuje ciąg do HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [Try... CATCH... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Odczytywanie z oraz zapisywanie do rejestru](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
