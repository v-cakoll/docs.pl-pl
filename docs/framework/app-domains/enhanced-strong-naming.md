---
title: Poprawa silnego nazywania
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf4a8df87cd507f2bfb17086e83dc8374a22fe71
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746894"
---
# <a name="enhanced-strong-naming"></a>Poprawa silnego nazywania
Podpis silnej nazwy jest mechanizmem tożsamości w programie .NET Framework do identyfikowania zestawów. Jest zwykle używany do sprawdzania integralności danych są przekazywane z autora (osoby podpisującej) do adresata (weryfikatora) podpis cyfrowy klucza publicznego. Ta sygnatura jest używana jako unikatową tożsamość zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne. Zestaw jest podpisany jako część procesu kompilacji, a następnie zweryfikować po załadowaniu go.  
  
 Podpisy silnej nazwy pomagać w zapobieganiu strony złośliwych przed naruszeniem z zestawem i następnie ponowne podpisanie zestawu z oryginalnego podpisującego klucza. Jednak kluczy silnej nazwy nie mogą zawierać żadnych wiarygodnych informacji o wydawcy ani one zawierać hierarchii certyfikatów. Podpisu silnej nazwy nie gwarantuje wiarygodności osoby podpisującej zestawu lub wskazuje, czy osoba była uzasadnionych właściciela klucza; Wskazuje on tylko, że właściciel klucza podpisana zestawu. Dlatego zaleca się używania podpisu silnej nazwy jako moduł weryfikacji zabezpieczeń dla ufających kodu innych firm. Microsoft Authenticode jest zalecanym sposobem uwierzytelniania kodu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Ograniczenia z konwencjonalnej silnej nazwy  
 Silnych nazw technologii używanej do wersji sprzed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ma następujące niedociągnięć:  
  
-   Klucze są stale zaatakowane i ulepszone technik i sprzętu ułatwiają wnioskować klucz prywatny z kluczem publicznym. Ochrona przed atakami, większe klucze są wymagane. Wersje programu .NET framework, przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zapewniają możliwość podpisać dowolny klawisz rozmiaru (rozmiar domyślny to 1024 bity), ale podpisywanie zestawu przy użyciu nowego klucza dzieli wszystkie pliki binarne, odwołujące się do starszych tożsamości zestawu. W związku z tym jest bardzo trudne do uaktualnienia rozmiar klucza podpisywania, jeśli chcesz zachować zgodność.  
  
-   Podpisywanie silną nazwą obsługuje tylko algorytm SHA-1. Ostatnio odnaleziono SHA-1 być nieodpowiednie dla bezpiecznych aplikacji wyznaczania wartości skrótu. W związku z tym silniejszego algorytmu (SHA-256 lub nowszego) jest konieczne. Istnieje możliwość, że SHA-1 spowoduje utratę stałego zgodne ze standardem FIPS, które przedstawia problemy dla tych, którzy korzystać tylko algorytmy i oprogramowania zgodne ze standardem FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Zalety rozszerzonych silnej nazwy  
 Główne zalety rozszerzonych silnych nazw są zgodność z istniejącym silne nazwy i możliwości, aby potwierdzić, że jedną tożsamość jest odpowiednikiem innego:  
  
-   Deweloperów, którzy mają istniejące zestawy podpisane można migrować tożsamości do algorytmów SHA-2, zachowując zgodność z zestawy, które odwołują się do starego tożsamości.  
  
-   Deweloperzy tworzący nowe zestawy i nie są związane z istniejącym podpisów silnej nazwy za pomocą bardziej bezpieczne algorytmy SHA-2 i zarejestrować zestawy zawsze mają.  
  
## <a name="using-enhanced-strong-names"></a>Przy użyciu rozszerzonych silnej nazwy  
 Kluczy silnej nazwy składają się z klucza podpisu i klucz tożsamości. Zestaw jest podpisany przy użyciu klucza podpisu i jest identyfikowany za pomocą klucza tożsamości. Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], te dwa klucze były identyczne. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klucz tożsamości jest taka sama jak w starszych wersjach systemu .NET Framework, ale klucz podpisu jest rozszerzona o silniejszy algorytm wyznaczania wartości skrótu. Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości do tworzenia podpisu zaradczych.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut umożliwia metadanych zestawu do istniejącego klucza publicznego na użytek tożsamości zestawu, dzięki czemu stare odwołania do zestawów kontynuować pracę.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut używa zaradczych podpisu do zapewnienia, że właściciel nowego klucza podpisu jest również właściciela starego klucza tożsamości.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Podpisywanie za pomocą algorytmu SHA-2, bez klucza migracji  
 Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw bez podpisu silnej nazwy migracji:  
  
1.  (Jeśli to konieczne), należy wygenerować nowy klucz tożsamości.  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Wyodrębnij klucza publicznego tożsamości, a następnie określ, że algorytm SHA-2 powinny być używane podczas logowania przy użyciu tego klucza.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Opóźnione podpisywanie zestawu z pliku klucza publicznego tożsamości.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Ponowne podpisanie zestawu z pary kluczy pełnej tożsamości.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Podpisywanie za pomocą algorytmu SHA-2, migracja klucza  
 Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw za pomocą podpisu silnej nazwy zmigrowane.  
  
1.  Generowanie pary kluczy i podpis (Jeśli to konieczne).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Wyodrębnij klucz publiczny podpisu, a następnie określ, że algorytm SHA-2 powinny być używane podczas logowania przy użyciu tego klucza.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Wyodrębnij tożsamości klucza publicznego, który określa algorytm skrótu, który generuje sygnaturę zaradczych.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Generowanie parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu, a następnie dołącz atrybut do zestawu.  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  Opóźnione podpisywanie zestawu z kluczem publicznym tożsamości.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Pełni podpisać zestawu z pary kluczy podpisu.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
