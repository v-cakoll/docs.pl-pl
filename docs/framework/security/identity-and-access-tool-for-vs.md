---
title: Narzędzie tożsamości i dostępu dla programu Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 9216298889637780e79d1bfc7ac060458c745968
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170121"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Narzędzie tożsamości i dostępu dla programu Visual Studio 2012
W tym temacie opisano nowe narzędzie tożsamości i dostępu dla programu Visual Studio 11. To narzędzie można pobrać spod następującego adresu URL: [ https://go.microsoft.com/fwlink/?LinkID=245849 ](https://go.microsoft.com/fwlink/?LinkID=245849) lub bezpośrednio z poziomu programu Visual Studio 11, wyszukując "tożsamość" w Menedżerze rozszerzeń.  
  
 Narzędzie tożsamości i dostępu dla programu Visual Studio 11 znacznie upraszcza projektowanie aplikacji dzięki następującym głównym funkcjom:  
  
-   Za pomocą tego nowego narzędzia możesz tworzyć aplikacje przy użyciu typów projektów aplikacji internetowych i szybko integrować je z programem IIS.  
  
-   W odróżnieniu od uwierzytelniania mającego zapewnić samą ochronę, za pomocą tego nowego narzędzia możesz określić stronę wykrywania/kontroler w lokalnym obszarze głównym (lub dowolny inny punkt końcowy obsługujący uwierzytelnianie w aplikacji), a program WIF skonfiguruje wszystkie nieuwierzytelnione żądania do docierania tam zamiast przekierowywać je do usługi STS.  
  
-   To narzędzie zawiera usługę tokenu zabezpieczającego (STS), która jest uruchamiana na komputerze lokalnym z chwilą rozpoczęcia sesji debugowania. W związku z tym nie musisz już tworzyć niestandardowych projektów usługi STS i dostosowywać ich w celu uzyskania oświadczeń potrzebnych do testowania aplikacji. Typy i wartości oświadczeń są w pełni konfigurowalne.  
  
-   Typowe ustawienia możesz modyfikować bezpośrednio za pośrednictwem interfejsu użytkownika tego narzędzia, bez konieczności modyfikowania pliku web.config.  
  
-   Za pomocą jednego ekranu możesz ustanowić federację z usługą Active Directory Federation Services (AD FS) 2.0 (lub innymi dostawcami protokołu WS-Federation).  
  
-   Narzędzie wykorzystuje możliwości systemu Windows Azure Access Control Service (ACS) z prostą listę pól wyboru dla wszystkich dostawców tożsamości, które chcesz użyć: Facebook, Google, Live ID, Yahoo!, dowolny dostawca protokołu OpenID i wszystkich dostawców usługi WS-Federation. Wybierz swoich dostawców tożsamości, kliknij przycisk OK, a następnie naciśnij klawisz F5, i aplikacja i usługa ACS zostaną automatycznie skonfigurowane, a aplikacja testowa będzie obsługiwać usługę ACS.  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje programu WIF](../../../docs/framework/security/wif-features.md)
