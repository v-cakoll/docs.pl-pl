---
title: Odczytywanie z rejestru i zapisywanie w nim za pomocą przestrzeni nazw Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 10431b1ad40ed320541a22fb46cc8db6dbb775b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360075"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Odczytywanie z oraz zapisywanie do rejestru za pomocą przestrzeni nazw Microsoft.Win32 (Visual Basic)

Chociaż `My.Computer.Registry` należy uwzględnić podstawowe potrzeby podczas programowania w rejestrze, można również użyć <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> klas i w <xref:Microsoft.Win32> przestrzeni nazw .NET Framework.  
  
## <a name="keys-in-the-registry-class"></a>Klucze w klasie rejestru  

 <xref:Microsoft.Win32.Registry>Klasa dostarcza podstawowe klucze rejestru, których można użyć w celu uzyskania dostępu do podkluczy i ich wartości. Same klucze podstawowe są tylko do odczytu. W poniższej tabeli wymieniono i opisano siedem kluczy uwidacznianych przez <xref:Microsoft.Win32.Registry> klasę.  
  
|**Klucz**|**Opis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Definiuje typy dokumentów i właściwości skojarzone z tymi typami.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Zawiera informacje o konfiguracji sprzętu, które nie są specyficzne dla użytkownika.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Zawiera informacje o bieżących preferencjach użytkownika, takich jak zmienne środowiskowe.|  
|<xref:Microsoft.Win32.Registry.DynData>|Zawiera dynamiczne dane rejestru, takie jak używane przez sterowniki urządzeń wirtualnych.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Zawiera pięć podkluczy (sprzęt, SAM, zabezpieczenia, oprogramowanie i system) przechowujących dane konfiguracji dla komputera lokalnego.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Zawiera informacje o wydajności składników oprogramowania.|  
|<xref:Microsoft.Win32.Registry.Users>|Zawiera informacje o domyślnych preferencjach użytkownika.|  
  
> [!IMPORTANT]
> Bardziej bezpieczne jest zapisanie danych do bieżącego użytkownika ( <xref:Microsoft.Win32.Registry.CurrentUser> ) niż na komputerze lokalnym ( <xref:Microsoft.Win32.Registry.LocalMachine> ). Warunek, który jest zwykle określany jako "squatting", występuje, gdy tworzony klucz został wcześniej utworzony przez inny, prawdopodobnie złośliwy, proces. Aby tego uniknąć, należy użyć metody, takiej jak <xref:Microsoft.Win32.RegistryKey.GetValue%2A> , która zwraca, `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
## <a name="reading-a-value-from-the-registry"></a>Odczytywanie wartości z rejestru  

 Poniższy kod ilustruje sposób odczytywania ciągu z HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 Poniższy kod odczytuje, zwiększa, a następnie zapisuje ciąg do HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Try...Catch...Finally, instrukcja](../../../language-reference/statements/try-catch-finally-statement.md)
- [Odczytywanie z rejestru i zapisywanie w nim](reading-from-and-writing-to-the-registry.md)
- [Bezpieczeństwo i rejestr](security-and-the-registry.md)
