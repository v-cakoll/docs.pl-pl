---
title: Bezpieczeństwo i rejestr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 2eba9d177769b22de3f931bc7af4905a80e316b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359971"
---
# <a name="security-and-the-registry-visual-basic"></a>Bezpieczeństwo i rejestr (Visual Basic)

Na tej stronie omówiono implikacje zabezpieczeń przechowywania danych w rejestrze.  
  
## <a name="permissions"></a>Uprawnienia  

 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (listy kontroli dostępu).  
  
 Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji. Aby użyć tych właściwości, musisz mieć uprawnienia do odczytu i zapisu z <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, które kontroluje dostęp do zmiennych rejestru. Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń) jest to każdy kod zainstalowany na lokalnym dysku twardym użytkownika, który ma odpowiednie uprawnienia dostępu do rejestru. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.RegistryPermission> Klasa.  
  
 Zmienne rejestru nie powinny być przechowywane w lokalizacjach pamięci, w których kod nie <xref:System.Security.Permissions.RegistryPermission> może uzyskać do nich dostępu. Podobnie, podczas udzielania uprawnień należy przyznać minimalnych uprawnień niezbędnych do wykonania zadania.  
  
 Wartości dostępu do uprawnień rejestru są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> Wyliczenie. Poniższa tabela zawiera szczegółowe informacje o jej elementach członkowskich.  
  
|Wartość|Dostęp do zmiennych rejestru|  
|-----------|----------------------------------|  
|`AllAccess`|Tworzenie, odczytywanie i zapisywanie|  
|`Create`|Przycisk Utwórz|  
|`NoAccess`|Brak dostępu|  
|`Read`|Odczyt|  
|`Write`|Zapisywanie|  
  
## <a name="checking-values-in-registry-keys"></a>Sprawdzanie wartości w kluczach rejestru  

 Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp. Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu. Aby tego uniknąć, należy użyć `GetValue` metody. Zwraca `Nothing` , jeśli klucz jeszcze nie istnieje.  
  
> [!IMPORTANT]
> Podczas odczytywania rejestru z aplikacji sieci Web tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Odczytywanie z rejestru i zapisywanie w nim](reading-from-and-writing-to-the-registry.md)
