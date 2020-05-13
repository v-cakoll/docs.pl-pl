---
title: Poprawa silnego nazywania
description: Konwencjonalne sygnatury silnej nazwy dla zestawów w .NET Framework mają ograniczenia. Dowiedz się więcej o ulepszonym silnym nazewnictwie.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: 720eda86ef0555127da422b2f44a414e8bbfb1b7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378951"
---
# <a name="enhanced-strong-naming"></a>Poprawa silnego nazywania
Sygnatura silnej nazwy jest mechanizmem tożsamości w .NET Framework do identyfikowania zestawów. Jest to podpis cyfrowy klucza publicznego, który zwykle jest używany do weryfikacji integralności danych, które są przesyłane z nadawcy (osoby podpisującej) do adresata (weryfikatora). Ta sygnatura jest używana jako unikatowa tożsamość zestawu i zapewnia, że odwołania do zestawu nie są niejednoznaczne. Zestaw jest podpisany jako część procesu kompilacji, a następnie weryfikowany po jego załadowaniu.  
  
 Podpisy silnej nazwy uniemożliwiają złośliwym stronom manipulowanie zestawem, a następnie ponowne podpisywanie zestawu przy użyciu oryginalnego klucza osoby podpisującej. Jednak klucze o silnych nazwach nie zawierają żadnych wiarygodnych informacji o wydawcy ani nie zawierają hierarchii certyfikatów. Podpis silnej nazwy nie gwarantuje wiarygodności osoby, która podpisała zestaw lub wskazuje, czy osoba była uprawnionym właścicielem klucza; wskazuje tylko, że właściciel klucza podpisuje zestaw. W związku z tym nie zaleca się używania podpisu silnej nazwy jako modułu sprawdzania zabezpieczeń w celu zaufania kodu innej firmy. Microsoft Authenticode jest zalecanym sposobem uwierzytelniania kodu.  
  
## <a name="limitations-of-conventional-strong-names"></a>Ograniczenia konwencjonalnych silnych nazw  
 Technologia silnego nazewnictwa używana w wersjach przed .NET Framework 4,5 ma następujące braki:  
  
- Klucze są stale objęte atakami, a udoskonalone techniki i sprzęt ułatwiają wywnioskowanie klucza prywatnego z klucza publicznego. Aby chronić przed atakami, potrzebne są większe klucze. Wersje .NET Framework przed .NET Framework 4,5 zapewniają możliwość podpisania przy użyciu dowolnego klucza rozmiaru (domyślny rozmiar to 1024 bitów), ale podpisywanie zestawu z nowym kluczem spowoduje przerwanie wszystkich plików binarnych, które odwołują się do starszej tożsamości zestawu. W związku z tym jest niezwykle trudne do uaktualnienia rozmiaru klucza podpisywania, jeśli chcesz zachować zgodność.  
  
- Podpisywanie silnej nazwy obsługuje tylko algorytm SHA-1. Wcześniej stwierdzono, że algorytm SHA-1 jest nieodpowiedni dla bezpiecznych aplikacji do tworzenia skrótów. W związku z tym konieczny jest silniejszy algorytm (SHA-256 lub nowszy). Istnieje możliwość, że algorytm SHA-1 utraci swoją pozycję zgodną ze standardem FIPS, co może spowodować problemy dla tych, którzy zdecydują się używać tylko oprogramowania zgodnego ze standardem FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Zalety ulepszonych silnych nazw  
 Główne zalety ulepszonych silnych nazw są zgodne ze wstępnie istniejącymi silnymi nazwami i możliwość stwierdzenia, że jedna tożsamość jest równoważna z inną:  
  
- Deweloperzy, którzy posiadają istniejące podpisane zestawy, mogą migrować swoje tożsamości do algorytmów SHA-2 przy zachowaniu zgodności z zestawami, które odwołują się do starych tożsamości.  
  
- Deweloperzy, którzy tworzą nowe zestawy i nie są zainteresowani istniejącymi sygnaturami silnej nazwy, mogą korzystać z bezpieczniejszych algorytmów SHA-2 i podpisywać zestawy w taki sam sposób, jak zawsze.  
  
## <a name="use-enhanced-strong-names"></a>Użyj ulepszonych silnych nazw  
 Klucze silnej nazwy składają się z klucza podpisu i klucza tożsamości. Zestaw jest podpisany przy użyciu klucza podpisu i jest identyfikowany przez klucz tożsamości. Przed .NET Framework 4,5 te dwa klucze były takie same. Począwszy od .NET Framework 4,5, klucz tożsamości pozostaje taki sam jak w starszych wersjach .NET Framework, ale klucz podpisu zostanie rozszerzony przy użyciu silniejszego algorytmu wyznaczania wartości skrótu. Ponadto klucz podpisu jest podpisany przy użyciu klucza tożsamości w celu utworzenia podpisu licznika.  
  
 Ten <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut umożliwia metadanych zestawu użycie istniejącego klucza publicznego dla tożsamości zestawu, co pozwala na kontynuowanie pracy przez stare odwołania do zestawu.  Ten <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut używa sygnatury licznika, aby upewnić się, że właściciel nowego klucza podpisu jest również właścicielem starego klucza tożsamości.  
  
### <a name="sign-with-sha-2-without-key-migration"></a>Podpisz przy użyciu algorytmu SHA-2 bez migracji klucza  
 Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw bez migrowania sygnatury silnej nazwy:  
  
1. Generuj nowy klucz tożsamości (w razie potrzeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. Wyodrębnij klucz publiczny tożsamości i określ, że algorytm SHA-2 powinien być używany podczas podpisywania przy użyciu tego klucza.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. Opóźnij podpisanie zestawu przy użyciu pliku klucza publicznego tożsamości.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. Ponowne podpisywanie zestawu za pomocą pary kluczy pełnej tożsamości.  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a>Logowanie przy użyciu algorytmu SHA-2 z migracją klucza  
 Uruchom następujące polecenia z wiersza polecenia, aby podpisać zestaw za pomocą zmigrowanego podpisu silnej nazwy.  
  
1. Wygeneruj parę kluczy tożsamości i sygnatury (w razie potrzeby).  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. Wyodrębnij klucz publiczny podpisu i określ, że algorytm SHA-2 powinien być używany podczas podpisywania przy użyciu tego klucza.  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. Wyodrębnij klucz publiczny tożsamości, który określa algorytm wyznaczania wartości skrótu, który generuje sygnaturę licznika.  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. Generuj parametry dla <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybutu i Dołącz atrybut do zestawu.  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    Daje to wynik podobny do poniższego.

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

    Dane wyjściowe można następnie przekształcić do atrybucie AssemblySignatureKeyAttribute określono.

    ```
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. Opóźnij podpisanie zestawu przy użyciu klucza publicznego tożsamości.  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. W pełni podpisz zestaw za pomocą pary kluczy podpisu.  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
