---
title: Poprawa silnego nazywania
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 1d582513b10de88e4e5b9b9ef8c338599d6980f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141168"
---
# <a name="enhanced-strong-naming"></a>Poprawa silnego nazywania
Podpis silnej nazwy jest mechanizmtożsamości w .NET Framework do identyfikowania zestawów. Jest to podpis cyfrowy klucza publicznego, który jest zwykle używany do weryfikacji integralności danych przekazywanych z inicjator (sygnatariusz) do odbiorcy (weryfikatora). Ten podpis jest używany jako unikatowa tożsamość dla zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne. Zestaw jest podpisany jako część procesu kompilacji, a następnie weryfikowany po załadowaniu.  
  
 Silne podpisy nazw zapobiegają manipulowaniu przez złośliwe strony zestawem, a następnie ponownepodpisywanie zestawu przy użyciu klucza oryginalnego sygnatariusza. Jednak silne klucze nazw nie zawierają żadnych wiarygodnych informacji o wydawcy, ani nie zawierają hierarchii certyfikatów. Silny podpis nie gwarantuje wiarygodności osoby, która podpisała zgromadzenie, ani nie wskazuje, czy osoba ta była prawowitym właścicielem klucza; wskazuje tylko, że właściciel klucza podpisał zestaw. W związku z tym nie zaleca się używania podpisu silnej nazwy jako sprawdzania poprawności zabezpieczeń dla ufania kodowi innej firmy. Microsoft Authenticode to zalecany sposób uwierzytelniania kodu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Ograniczenia konwencjonalnych silnych nazw  
 Technologia silnego nazewnictwa używana w wersjach przed .NET Framework 4.5 ma następujące wady:  
  
- Klucze są stale atakowane, a ulepszone techniki i sprzęt ułatwiają wywnioskowanie klucza prywatnego z klucza publicznego. Aby zabezpieczyć się przed atakami, konieczne są większe klucze. Wersje .NET Framework przed .NET Framework 4.5 zapewniają możliwość podpisywania za pomocą dowolnego klucza rozmiaru (domyślny rozmiar to 1024 bity), ale podpisywanie zestawu za pomocą nowego klucza przerywa wszystkie pliki binarne, które odwołują się do starszej tożsamości zestawu. W związku z tym jest niezwykle trudne do uaktualnienia rozmiar klucza podpisywania, jeśli chcesz zachować zgodność.  
  
- Podpisywanie silnej nazwy obsługuje tylko algorytm SHA-1. Sha-1 niedawno stwierdzono, że nie odpowiednie dla bezpiecznych aplikacji mieszania. W związku z tym silniejszy algorytm (SHA-256 lub więcej) jest konieczne. Jest możliwe, że SHA-1 straci swoją pozycję zgodną ze standardem FIPS, co stanowiłoby problemy dla tych, którzy zdecydują się używać tylko oprogramowania i algorytmów zgodnych z FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Zalety wzmocnionych silnych nazw  
 Główne zalety wzmocnionych silnych nazw to zgodność z istniejącymi wcześniej silnymi nazwami i możliwość twierdzenia, że jedna tożsamość jest równoważna innej:  
  
- Deweloperzy, którzy mają wcześniej podpisane zestawy można migrować ich tożsamości do algorytmów SHA-2 przy zachowaniu zgodności z zestawów, które odwołują się do starych tożsamości.  
  
- Deweloperzy, którzy tworzą nowe zestawy i nie są zaniepokojeni wcześniej istniejących podpisów silnej nazwy można użyć bardziej bezpieczne algorytmy SHA-2 i podpisać zestawy, jak zawsze mają.  
  
## <a name="use-enhanced-strong-names"></a>Używanie rozszerzonych silnych nazw  
 Silne klucze nazw składają się z klucza podpisu i klucza tożsamości. Zestaw jest podpisany przy pomocą klucza podpisu i jest identyfikowany przez klucz tożsamości. Przed .NET Framework 4.5 te dwa klucze były identyczne. Począwszy od .NET Framework 4.5, klucz tożsamości pozostaje taki sam jak we wcześniejszych wersjach .NET Framework, ale klucz podpisu jest rozszerzony o silniejszy algorytm mieszania. Ponadto klucz podpisu jest podpisany przy pomocą klucza tożsamości w celu utworzenia kontrpodpisu.  
  
 Atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> umożliwia metadanych zestawu do korzystania z istniejącego klucza publicznego dla tożsamości zestawu, co pozwala stare odwołania do zestawu, aby kontynuować pracę.  Atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> używa kontrpodpisu, aby upewnić się, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Podpisz za pomocą SHA-2 bez migracji kluczy  
 Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw bez migracji podpisu silnej nazwy:  
  
1. Wygeneruj nowy klucz tożsamości (jeśli to konieczne).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Wyodrębnij klucz publiczny tożsamości i określ, że algorytm SHA-2 powinien być używany podczas podpisywania za pomocą tego klucza.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Delay-sign zestawu z pliku klucza publicznego tożsamości.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Ponownie podpisz zestaw za pomocą pełnej pary kluczy tożsamości.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Podpisz za pomocą SHA-2 z migracją kluczy  
 Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw z migrowanym podpisem silnej nazwy.  
  
1. Generowanie pary kluczy tożsamości i podpisu (jeśli to konieczne).  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. Wyodrębnij klucz publiczny podpisu i określ, że algorytm SHA-2 powinien być używany podczas podpisywania za pomocą tego klucza.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Wyodrębnij klucz publiczny tożsamości, który określa algorytm mieszania, który generuje kontrpodpis.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Wygeneruj <xref:System.Reflection.AssemblySignatureKeyAttribute> parametry atrybutu i dołącz atrybut do złożenia.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Daje to dane wyjściowe podobne do następujących.

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    Dane wyjściowe można następnie przekształcić w AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Delay-sign zestawu z kluczem publicznym tożsamości.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. W pełni podpisać zestaw z pary kluczy podpisu.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
