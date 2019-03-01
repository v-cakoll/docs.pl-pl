---
title: Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 9b88257dcdd80c5ec5e81e0c3c20822157907fa5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966271"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)
Mimo że `My.Computer.Registry` powinna obejmować potrzeb podstawowe, gdy Programowanie w odniesieniu do rejestru, można również użyć <xref:Microsoft.Win32.Registry> i <xref:Microsoft.Win32.RegistryKey> klas w <xref:Microsoft.Win32> przestrzeń nazw [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
## <a name="keys-in-the-registry-class"></a>Klucze rejestru klasy  
 <xref:Microsoft.Win32.Registry> Klasa zapewnia kluczy rejestru podstawowej, które mogą być używane do dostępu podklucze i wartości. Klawisze podstawowej są tylko do odczytu. Poniższej tabeli wymieniono i opisano klucze siedem udostępnianych przez <xref:Microsoft.Win32.Registry> klasy.  
  
|**Key**|**Opis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definiuje typy dokumentów i właściwości skojarzone z tych typów.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Zawiera informacje o konfiguracji sprzętu, który nie jest specyficzne dla użytkownika.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Zawiera informacje o bieżącym preferencje użytkownika, takie jak zmienne środowiskowe.|  
|<xref:Microsoft.Win32.Registry.DynData>|Zawiera dane rejestru dynamicznych, takie jak używanej przez sterowniki urządzeń wirtualnych.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Zawiera pięć podkluczy (sprzętu, SAM, zabezpieczeń, oprogramowania i systemu) używane do przechowywania danych konfiguracji na komputerze lokalnym.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Zawiera informacje o wydajności dla składników oprogramowania.|  
|<xref:Microsoft.Win32.Registry.Users>|Zawiera informacje o domyślnych preferencji użytkownika.|  
  
> [!IMPORTANT]
>  Bezpieczniej jest do zapisywania danych z bieżącym użytkownikiem (<xref:Microsoft.Win32.Registry.CurrentUser>) niż na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>). Warunek, który jest zwykle określane jako "tureckie" występuje, gdy tworzysz klucz został wcześniej utworzony przez inną, potencjalnie złośliwego procesu. Aby temu zapobiec, należy użyć metody, takie jak <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, która zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
## <a name="reading-a-value-from-the-registry"></a>Odczytywanie wartości z rejestru  
 Poniższy kod przedstawia sposób odczytywania ciągu z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Poniższy kod odczytuje przyrostów, a następnie zapisuje ciąg do HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
