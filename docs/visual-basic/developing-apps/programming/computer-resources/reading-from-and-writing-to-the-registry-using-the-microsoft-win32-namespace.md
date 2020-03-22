---
title: Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345498"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)

Chociaż `My.Computer.Registry` należy pokryć podstawowe potrzeby podczas programowania w <xref:Microsoft.Win32.Registry> rejestrze, można również użyć i <xref:Microsoft.Win32.RegistryKey> klas w obszarze <xref:Microsoft.Win32> nazw .NET Framework.  
  
## <a name="keys-in-the-registry-class"></a>Klucze w klasie rejestru  

 Klasa <xref:Microsoft.Win32.Registry> dostarcza podstawowe klucze rejestru, które mogą służyć do uzyskiwania dostępu do podkluczy i ich wartości. Same klucze podstawowe są tylko do odczytu. W poniższej tabeli wymieniono i <xref:Microsoft.Win32.Registry> opisano siedem kluczy udostępniane przez klasę.  
  
|**Klucz**|**Opis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definiuje typy dokumentów i właściwości skojarzone z tymi typami.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Zawiera informacje o konfiguracji sprzętu, które nie są specyficzne dla użytkownika.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Zawiera informacje o bieżących preferencjach użytkownika, takich jak zmienne środowiskowe.|  
|<xref:Microsoft.Win32.Registry.DynData>|Zawiera dynamiczne dane rejestru, takie jak używane przez sterowniki urządzeń wirtualnych.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Zawiera pięć podkluczy (Sprzęt, SAM, Zabezpieczenia, Oprogramowanie i System), które przechowują dane konfiguracyjne dla komputera lokalnego.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Zawiera informacje o wydajności składników oprogramowania.|  
|<xref:Microsoft.Win32.Registry.Users>|Zawiera informacje o domyślnych preferencjach użytkownika.|  
  
> [!IMPORTANT]
> Bezpieczniejsze jest zapisywanie danych do<xref:Microsoft.Win32.Registry.CurrentUser>bieżącego użytkownika (<xref:Microsoft.Win32.Registry.LocalMachine>) niż do komputera lokalnego ( ). Warunek, który jest zazwyczaj określany jako "kucanie" występuje, gdy klucz, który tworzysz został wcześniej utworzony przez inny, prawdopodobnie złośliwy, proces. Aby temu zapobiec, należy użyć metody, <xref:Microsoft.Win32.RegistryKey.GetValue%2A>takiej `Nothing` jak , która zwraca, jeśli klucz jeszcze nie istnieje.  
  
## <a name="reading-a-value-from-the-registry"></a>Odczytywanie wartości z rejestru  

 Poniższy kod pokazuje, jak odczytać ciąg z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Poniższy kod odczytuje, przyrosty, a następnie zapisuje ciąg do HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally, instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Bezpieczeństwo i rejestr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
