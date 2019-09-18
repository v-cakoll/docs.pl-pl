---
title: Sprawdzanie poprawności rejestru nazwy dostawcy
ms.date: 03/30/2017
ms.assetid: c4644dd1-dead-48ff-abeb-7bffae69a6ac
ms.openlocfilehash: dc7da9d3dc4ab696d8c27d8e12583b8d06e747fe
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045314"
---
# <a name="validating-issuer-name-registry"></a>Sprawdzanie poprawności rejestru nazwy dostawcy
Rozszerzenie Validating Issuer Name Registry (VINR) dla programu Windows Identity Foundation umożliwia aplikacjom wielodostępnym upewnienie się, że przychodzący token został wystawiony przez zaufanego dostawcę dzierżawców i tożsamości. Ta funkcja jest szczególnie przydatna w przypadku aplikacji wielodostępnych, które używają usługi Active Directory systemu Microsoft Azure, ponieważ wszystkie tokeny wystawione przez tę usługę są podpisywane za pomocą tego samego certyfikatu. W celu dokonania rozróżnienia między żądaniami od wielu dzierżawców, którzy korzystają z tego samego certyfikatu — i w związku z tym mają ten sam odcisk palca — aplikacja musi utrwalić nazwę wystawcy dla każdego dzierżawcy, aby wykonać logikę weryfikacji. Rozszerzenie VINR oferuje tę funkcję, a ponadto pozwala na dodawanie niestandardowej logiki weryfikacji lub przechowywanie danych rejestru dostawcy w lokalizacjach innych niż plik konfiguracji. To rozszerzenie można dodać do potoku programu WIF aplikacji lub można go używać niezależnie.  
  
 Rozszerzenie VINR jest dostępne jako pakiet NuGet. Aby uzyskać więcej informacji, zobacz artykuł [pobieranie informacji o sprawdzaniu poprawności nazwy wystawcy wydawcy](downloading-the-validating-issuer-name-registry-package.md) .  
  
## <a name="scenarios"></a>Scenariusze  
 Rozszerzenie VINR umożliwia realizację następującego podstawowego scenariusza:  
  
- **Weryfikowanie tokenu w aplikacji**wielodostępnej: W tym scenariuszu firma o nazwie litware opracowała aplikację z wieloma dzierżawcami, która używa dostawcy tożsamości, takiego jak Windows Azure AD. Ta aplikacja służy dwóm klientom: Firma Contoso i fabrikam. Gdy użytkownik z firmy Fabrikam uwierzytelnia się przed aplikacją firmy Litware, powstały token z usługi AD systemu Microsoft Azure zostaje podpisany przy użyciu standardowego certyfikatu i żądanie zostaje wystawione przez firmę Fabrikam. Aplikacja musi sprawdzić, czy zarówno nazwa wystawcy, jak i token są prawidłowe, i musi odróżniać zapytania z firmy Contoso, które są podpisane za pomocą tego samego certyfikatu z usługi AD systemu Microsoft Azure. Rozszerzenie VINR ułatwia aplikacji firmy Litware odróżnianie i weryfikację żądań od wielu dzierżawców, takich jak Contoso i Fabrikam.  
  
## <a name="features"></a>Funkcje  
 Rozszerzenie VINR oferuje następujące funkcje:  
  
- **Nazwa wystawcy i walidacja tokenu dla aplikacji wielodostępnych**: Sprawdza poprawność tokenu przychodzącego przez zweryfikowanie nazwy wystawcy (dzierżawcy) oraz tego, czy token został podpisany za pomocą ważnego certyfikatu od dostawcy tożsamości.  
  
- **Rozszerzalność dla logiki niestandardowego sprawdzania poprawności i magazynów danych**: Zapewnia rozszerzalność, aby wstrzyknąć własną logikę walidacji i określić magazyn danych inny niż domyślny plik konfiguracji.
