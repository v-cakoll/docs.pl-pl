---
title: Bezpieczeństwo i rejestr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839361"
---
# <a name="security-and-the-registry-visual-basic"></a>Bezpieczeństwo i rejestr (Visual Basic)
Ta strona zawiera omówienie ryzyko związane z przechowywaniem danych w rejestrze.  
  
## <a name="permissions"></a>Uprawnienia  
 Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (listy kontroli dostępu).  
  
 Praca z rejestru może naruszyć bezpieczeństwo, zezwalając na niewłaściwe dostęp do zasobów systemowych lub informacje chronione. Aby korzystać z tych właściwości, konieczne jest posiadanie Odczyt i zapis z <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, które kontrolują dostęp do zmiennych rejestru. Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń, to każdy kod zainstalowana na lokalnym dysku twardym użytkownika) ma niezbędne uprawnienia dostępu do rejestru. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.RegistryPermission> klasy.  
  
 Zmienne rejestru nie powinien być przechowywany w lokalizacji pamięci gdzie kodu bez <xref:System.Security.Permissions.RegistryPermission> mają do nich dostęp. Podobnie podczas nadawania uprawnień należy przyznać minimalne uprawnienia, które trzeba wykonać zadanie.  
  
 Uprawnienia dostępu do wartości są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia. W poniższej tabeli przedstawiono jej członków.  
  
|Wartość|Dostęp do zmiennych rejestru|  
|-----------|----------------------------------|  
|`AllAccess`|Tworzenia, odczytu i zapis|  
|`Create`|Create|  
|`NoAccess`|Brak dostępu|  
|`Read`|Odczyt|  
|`Write`|Write|  
  
## <a name="checking-values-in-registry-keys"></a>Sprawdzanie wartości w kluczach rejestru  
 Kiedy tworzysz wartość rejestru, musisz zdecydować, co należy zrobić, jeśli ta wartość już istnieje. Inny proces, fałszywy, być może już utworzył wartość i masz do niego dostęp. Dane są umieszczane w wartości rejestru, dane są dostępne dla innego procesu. Aby tego uniknąć, należy użyć `GetValue` metody. Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.  
  
> [!IMPORTANT]
>  Podczas odczytywania rejestru z aplikacji sieci Web, tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowane w aplikacji sieci Web.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Odczytywanie z rejestru i zapisywanie w nim](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
