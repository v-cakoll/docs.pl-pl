---
title: Bezpieczeństwo i rejestr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345485"
---
# <a name="security-and-the-registry-visual-basic"></a>Bezpieczeństwo i rejestr (Visual Basic)

Na tej stronie omówiono implikacje zabezpieczeń przechowywania danych w rejestrze.  
  
## <a name="permissions"></a>Uprawnienia  

 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (listy kontroli dostępu).  
  
 Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji. Aby użyć tych właściwości, musisz mieć uprawnienia do odczytu i zapisu z <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, które kontroluje dostęp do zmiennych rejestru. Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń) jest to każdy kod zainstalowany na lokalnym dysku twardym użytkownika, który ma odpowiednie uprawnienia dostępu do rejestru. Aby uzyskać więcej informacji, <xref:System.Security.Permissions.RegistryPermission> zobacz Klasa.  
  
 Zmienne rejestru nie powinny być przechowywane w lokalizacjach pamięci, w <xref:System.Security.Permissions.RegistryPermission> których kod nie może uzyskać do nich dostępu. Podobnie, podczas udzielania uprawnień należy przyznać minimalnych uprawnień niezbędnych do wykonania zadania.  
  
 Wartości dostępu do uprawnień rejestru są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> Wyliczenie. Poniższa tabela zawiera szczegółowe informacje o jej elementach członkowskich.  
  
|Wartość|Dostęp do zmiennych rejestru|  
|-----------|----------------------------------|  
|`AllAccess`|Tworzenie, odczytywanie i zapisywanie|  
|`Create`|Utwórz|  
|`NoAccess`|Brak dostępu|  
|`Read`|Odczyt|  
|`Write`|Zapisywanie|  
  
## <a name="checking-values-in-registry-keys"></a>Sprawdzanie wartości w kluczach rejestru  

 Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu. Aby tego uniknąć, należy użyć `GetValue` metody. Zwraca `Nothing` , jeśli klucz jeszcze nie istnieje.  
  
> [!IMPORTANT]
> Podczas odczytywania rejestru z aplikacji sieci Web tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
