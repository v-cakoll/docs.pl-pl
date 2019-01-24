---
title: Poprawa silnego nazywania
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a0b63e27a3eceb80d42d43eea321b0dc757ad69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688872"
---
# <a name="enhanced-strong-naming"></a>Poprawa silnego nazywania
Podpis silnej nazwy to mechanizm tożsamości w programie .NET Framework do identyfikowania zestawów. Jest podpis cyfrowy klucz publiczny, który jest zazwyczaj używany do sprawdzenia integralności danych przekazywanych od inicjatora (osoby podpisującej) do adresata (weryfikatora). Ta sygnatura jest używana jako unikatowa tożsamość dla zestawu i zapewnia, że odwołania do zestawu są jednoznaczne. Zestaw jest podpisywany jako część procesu kompilacji, a następnie weryfikowany po jego załadowaniu.  
  
 Podpisy silnej nazwy pozwalają zapobiec naruszeniu zestawu, a następnie ponownemu podpisywaniu zestawu za pomocą oryginalnego podpisującego klucza. Jednakże klucze o silnych nazwach nie zawierają żadnych wiarygodnych informacji o wydawcy ani zawierają hierarchii certyfikatów. Podpis silnej nazwy nie gwarantuje wiarygodności osoby, która podpisała zestaw ani nie wskazują, czy osoba była jest prawowitych właścicielem klucza; wskazuje tylko, że właściciela klucza podpisała zestaw. W związku z tym nie zalecamy używania podpisu silnej nazwy jako modułu sprawdzania zabezpieczeń dla ufającej kodu innych firm. Authenticode firmy Microsoft jest zalecanym sposobem uwierzytelniania kodu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Ograniczenia konwencjonalnych silnych nazw  
 Technologia silnego nazewnictwa wykorzystywana w wersjach przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ma następujące braki:  
  
-   Klucze są stale atakowane i techniki i sprzęt ułatwiają wywnioskować klucza prywatnego z klucza publicznego. Aby zabezpieczyć się przed atakami, kluczy są niezbędne. Wersje programu .NET framework przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zapewniają możliwość podpisywania z dowolnym rozmiarem klucza (rozmiar domyślny wynosi 1024 bity), ale podpisywanie zestawu z nowym kluczem przerywa wszystkie pliki binarne, które odwołują się do starszych tożsamości zestawu. W związku z tym, bardzo trudno jest uaktualnianie rozmiaru klucza podpisywania, jeśli chcesz zachować zgodność.  
  
-   Podpis silnej nazwy obsługuje tylko algorytm SHA-1. Ostatnio odnaleziono SHA-1 jako niewystarczający dla bezpiecznych aplikacji mieszania. Dlatego jest mocniejszy algorytm (SHA-256 lub większy) jest niezbędne. Istnieje możliwość, że algorytm SHA-1 spowoduje utratę stałego zgodne ze standardem FIPS, co przedstawiałoby problemy dla tych, którzy wolą używać tylko zgodne ze standardem FIPS oprogramowanie i algorytmów.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Zalety rozszerzonych silnych nazw  
 Głównymi zaletami rozszerzonych silnych nazw są zgodność z istniejącym silnymi nazwami i możliwość stwierdzenia, że jedna tożsamość jest równoważna z inną:  
  
-   Deweloperzy, którzy mają istniejące zestawy podpisane, mogą migrować swoją tożsamość do algorytmów SHA-2 przy zachowaniu zgodności z zestawy odwołujące się do starych tożsamości.  
  
-   Deweloperzy, którzy tworzą nowe zestawy i nie są związani z istniejącym podpisem silnej nazwy można użyć bardziej bezpieczne algorytmów SHA-2 i podpisywać zestawy tak jak dotychczas.  
  
## <a name="using-enhanced-strong-names"></a>Używanie rozszerzonych silnych nazw  
 Klucze silnej nazwy składają się z klucza podpisu i klucza tożsamości. Zestaw jest podpisany za pomocą klucza podpisu i jest identyfikowany przez klucz tożsamości. Przed [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], te dwa klucze były identyczne. Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], klucz tożsamości pozostaje taki sam jak w starszych wersjach .NET Framework, ale klucz podpisu jest rozszerzony o mocniejszy algorytm wyznaczania wartości skrótu. Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości do utworzenia kontrsygnatury.  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybut pozwala metadanym zestawu do istniejącego klucza publicznego na użytek tożsamość zestawu, co pozwala starym odwołaniom do zestawu na kontynuowanie pracy.  <xref:System.Reflection.AssemblySignatureKeyAttribute> Atrybutu używa kontrsygnatury do zapewnienia, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Podpisywanie za pomocą algorytmu SHA-2, bez migracji kluczy  
 Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw bez przenoszenia podpisu silnej nazwy:  
  
1.  (Jeśli jest to konieczne), należy wygenerować nowy klucz tożsamości.  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Wyodrębnij klucz publiczny tożsamości, a następnie określić, że algorytm SHA-2 powinien używane podczas logowania przy użyciu tego klucza.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Opóźnij podpisanie zestawu z tożsamością pliku klucza publicznego.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Ponowne Podpisz zestaw parą kluczy pełnej tożsamości.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Podpisywanie za pomocą algorytmu SHA-2, z migracją kluczy  
 Uruchom następujące polecenia z okna wiersza polecenia, aby podpisać zestaw przy użyciu przeniesionego podpisu silnej nazwy.  
  
1.  Generowanie pary kluczy tożsamości i podpisu (jeśli jest to konieczne).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Wyodrębnij klucz publiczny podpisu i określić, że algorytm SHA-2 powinien używane podczas logowania przy użyciu tego klucza.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Wyodrębnij klucz publiczny tożsamości, który określa algorytm wyznaczania wartości skrótu, który generuje kontrsygnaturę.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Wygeneruj parametry <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu i Dołącz atrybut do zestawu.  
  
    ```  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    To generuje dane wyjściowe podobne do następujących.

    ```
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

    To danych wyjściowych może następnie zostać przekształcone na AssemblySignatureKeyAttribute.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5.  Opóźnij podpisanie zestawu z tożsamością klucza publicznego.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  W pełni Podpisz zestaw za pomocą pary kluczy podpisu.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
