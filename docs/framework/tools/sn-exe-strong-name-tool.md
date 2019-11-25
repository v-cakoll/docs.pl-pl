---
title: Sn.exe (Narzędzie silnych nazw)
ms.date: 03/30/2017
helpviewer_keywords:
- public keys, signing files
- Strong Name tool
- Sn.exe
- assemblies [.NET Framework], signing
- signing files
- strong-named assemblies, signing files
- key pairs for signing files
ms.assetid: c1d2b532-1b8e-4c7a-8ac5-53b801135ec6
ms.openlocfilehash: 90cad6529b3ac2a8afedaca0c43d5c7561dcf9e6
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138962"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Narzędzie silnych nazw)
Narzędzie silnych nazw (SN. exe) pomaga podpisywać zestawy o [silnych nazwach](../../standard/assembly/strong-named.md). Sn.exe dostarcza opcje do zarządzania kluczami, generowania podpisów i ich weryfikacji.  
  
> [!WARNING]
> Nie należy polegać na silnych nazwach zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

 Aby uzyskać więcej informacji na temat silnych nazw i zestawów o silnych nazwach, zobacz [zestawy o silnych](../../standard/assembly/strong-named.md) nazwach i [instrukcje: podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).  
  
 Narzędzie silnych nazw jest automatycznie instalowane z Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  

> [!NOTE]
> Na komputerach 64-bitowych Uruchom 32-bitową wersję SN. exe przy użyciu wiersz polecenia dla deweloperów dla programu Visual Studio i wersji 64-bitowej przy użyciu wiersza polecenia programu Visual Studio x64 Win64. 
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dane w celu przeprowadzenia migracji klucza tożsamości do klucza podpisu z pliku.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dane w celu przeprowadzenia migracji klucza tożsamości do klucza podpisu z kontenera kluczy.|  
|`-c [csp]`|Określa domyślnego dostawcę usług kryptograficznych (CSP) do podpisywania silnymi nazwami. To ustawienie odnosi się do całego komputera. Jeśli nie określisz nazwy CSP, Sn.exe wyczyści bieżące ustawienie.|  
|`-d container`|Usuwa określony kontener kluczy z CSP silnej nazwy.|  
|`-D assembly1 assembly2`|Weryfikuje, czy dwa zestawy różnią się tylko podpisem. Jest to często używane jako sprawdzenie po ponownym podpisaniu zestawu inną parą kluczy.|  
|`-e assembly outfile`|Wyodrębnia klucz publiczny z *zestawu* i zapisuje go w *pliku.*|  
|`-h`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`-i infile container`|Instaluje parę kluczy z *infile* w określonym kontenerze kluczy. Kontener kluczy mieści się w CSP silnej nazwy.|  
|`-k [keysize] outfile`|Generuje nowy klucz <xref:System.Security.Cryptography.RSACryptoServiceProvider> o określonym rozmiarze i zapisuje go w określonym pliku.  Oba klucze, publiczny i prywatny, są zapisywane do pliku.<br /><br /> Jeśli nie określono rozmiaru klucza, w przypadku gdy zainstalowany jest ulepszony dostawca kryptograficzny firmy Microsoft, domyślnie generowany jest 1024-bitowy klucz; w przeciwnym wypadku, generowany jest 512-bitowy klucz.<br /><br /> Parametr *rozmiaru* klucza obsługuje długości kluczy z 384 bitów do 16 384 bitów w przyrostach wynoszących 8 bitów, jeśli jest zainstalowany zaawansowany dostawca usług kryptograficznych firmy Microsoft.  Obsługuje on długości kluczy od 384 bitów do 512 bitów rosnąco co 8 bitów, jeśli zainstalowany jest podstawowy dostawca kryptograficzny firmy Microsoft.|  
|`-m [y|n]`|Określa, czy kontenery kluczy są specyficzne dla komputera, czy dla użytkownika. W przypadku określenia wartości *y*kontenery kluczy są specyficzne dla komputera. Jeśli określisz *n*, kontenery kluczy są specyficzne dla użytkownika.<br /><br /> Jeśli nie podano ani y ani n, ta opcja wyświetla bieżące ustawienie.|  
|`-o infile [outfile]`|Wyodrębnia klucz publiczny z *infile* i zapisuje go w pliku CSV. Poszczególne bajty klucza publicznego są rozdzielone przecinkami. Ten format jest użyteczny dla trwale zakodowanych odwołań do kluczy, takich jak zainicjowane tablice w kodzie źródłowym. Jeśli nie określisz *pliku*, ta opcja umieszcza dane wyjściowe w Schowku. **Uwaga:**  Ta opcja nie sprawdza, czy dane wejściowe są tylko kluczem publicznym. Jeśli `infile` zawiera parę kluczy z kluczem prywatnym, klucz prywatny również zostanie wyodrębniony.|  
|`-p infile outfile [hashalg]`|Wyodrębnia klucz publiczny z pary kluczy w *pliku infile* i zapisuje go w *pliku*, opcjonalnie używając algorytmu RSA określonego przez *hashAlg*. Ten klucz publiczny może służyć do opóźnienia podpisywania zestawu przy użyciu opcji **/delaysign +** i **/KeyFile** [konsolidatora zestawu (Al. exe)](al-exe-assembly-linker.md). Gdy zestaw jest podpisany z opóźnieniem, w czasie kompilacji ustawiany jest tylko klucz publiczny i rezerwowana jest przestrzeń w pliku na późniejsze dodanie podpisu, gdy znany będzie klucz prywatny.|  
|`-pc container outfile [hashalg]`|Wyodrębnia klucz publiczny z pary kluczy w *kontenerze* i zapisuje je w *pliku*. W przypadku użycia opcji *hashAlg* algorytm RSA jest używany do wyodrębniania klucza publicznego.|  
|`-Pb [y|n]`|Określa, czy wymuszona jest zasada obejścia silnej nazwy. Jeśli określisz wartość *y*, silne nazwy dla zestawów pełnego zaufania nie są weryfikowane podczas ładowania do <xref:System.AppDomain>pełnego zaufania. Jeśli określisz *n*, silne nazwy są weryfikowane pod kątem poprawności, ale nie dla określonej silnej nazwy. <xref:System.Security.Permissions.StrongNameIdentityPermission> nie ma wpływu na zestawy z pełnym zaufaniem. Musisz wykonać swoje własne sprawdzenie dopasowania silnej nazwy.<br /><br /> Jeśli nie `y` ani `n` jest określony, ta opcja wyświetla bieżące ustawienie. Wartość domyślna to `y`. **Uwaga:**  Na komputerach 64-bitowych należy ustawić ten parametr zarówno w przypadku wystąpienia 32-bitowego, jak i 64-bit programu SN. exe.|  
|`-q[uiet]`|Określa tryb cichy; pomija wyświetlanie komunikatów o powodzeniu.|  
|`-R[a] assembly infile`|Podpisuje wcześniej podpisany lub podpisany z opóźnieniem zestaw za pomocą pary kluczy w *pliku infile*.<br /><br /> Jeśli jest używany **-RA** , skróty są ponownie obliczane dla wszystkich plików w zestawie.|  
|`-Rc[a] assembly container`|Podpisuje wcześniej podpisany lub podpisany z opóźnieniem zestaw za pomocą pary kluczy w *kontenerze*.<br /><br /> If **-RCA** jest używany, skróty są ponownie obliczane dla wszystkich plików w zestawie.|  
|`-Rh assembly`|Oblicza ponownie skróty dla wszystkich plików w zestawie.|  
|`-t[p] infile`|Wyświetla token dla klucza publicznego przechowywanego w *pliku infile*. Zawartość *infile* musi być kluczem publicznym wcześniej wygenerowanym z pliku pary kluczy przy użyciu **-p**.  Nie używaj opcji **-t [p]** , aby wyodrębnić token bezpośrednio z pliku pary kluczy.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe języka wspólnego zapisuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. Opcja **-TP** wyświetla klucz publiczny oprócz tokenu. Jeśli atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> został zastosowany do zestawu, token ma wartość klucz tożsamości i zostanie wyświetlona nazwa algorytmu wyznaczania wartości skrótu i klucza tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-T[p] assembly`|Wyświetla token klucza publicznego dla *zestawu.* *Zestaw* musi być nazwą pliku, który zawiera manifest zestawu.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe przechowuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. Opcja **-TP** wyświetla klucz publiczny oprócz tokenu. Jeśli atrybut <xref:System.Reflection.AssemblySignatureKeyAttribute> został zastosowany do zestawu, token ma wartość klucz tożsamości i zostanie wyświetlona nazwa algorytmu wyznaczania wartości skrótu i klucza tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-TS assembly infile`|Test — podpisuje podpisany lub częściowo podpisany *zestaw* za pomocą pary kluczy w *pliku infile*.|  
|`-TSc assembly container`|Test — podpisuje podpisany lub częściowo podpisany *zestaw* za pomocą pary kluczy w *kontenerze*kontenerów kluczy.| 
|`-v assembly`|Weryfikuje silną nazwę w *zestawie*, gdzie *Assembly* jest nazwą pliku, który zawiera manifest zestawu.|  
|`-vf assembly`|Weryfikuje silną nazwę w *zestawie.* W przeciwieństwie do opcji **-v** , funkcja **-funkcji wirtualnej** wymusza weryfikację, nawet jeśli jest wyłączona przy użyciu opcji **-VR** .|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Tworzy plik wpisów rejestracji (reg), którego można użyć do zarejestrowania określonego zestawu, aby pomijał weryfikację. Reguły nazewnictwa zestawów, które mają zastosowanie do opcji **-VR** , mają również zastosowanie do **– VK** . Aby uzyskać informacje o opcjach *userlist* i *infile* , zobacz **-VR** .|  
|`-Vl`|Wyświetla listę bieżących ustawień dla weryfikacji silnych nazw na tym komputerze.|  
|`-Vr  assembly [userlist] [infile]`|Rejestruje *zestaw* do pomijania weryfikacji. Opcjonalnie można określić listę rozdzielonych przecinkami nazw użytkownika, do których powinno zostać zastosowane pominięcie weryfikacji. W przypadku określenia *infile*weryfikacja pozostanie włączona, ale klucz publiczny w *pliku infile* jest używany w operacjach weryfikacji. Możesz określić *zestaw* w formularzu *\*, StrongName,* aby zarejestrować wszystkie zestawy z określoną silną nazwą. Dla elementu *StrongName*Określ ciąg znaków szesnastkowych reprezentujących postać tokenu w postaci klucza publicznego. Zobacz opcje **-t** i **-t** , aby wyświetlić token klucza publicznego. **Przestroga:**  Tej opcji należy używać tylko podczas projektowania. Dodanie zestawu, który będzie pomijał listę weryfikacji, tworzy lukę w zabezpieczeniach. Złośliwy zestaw mógłby użyć w pełni określonej nazwy (nazwy zestawu, wersji, kultury i tokenu klucza publicznego) zestawu dodanego do listy pomijania weryfikacji, aby ukryć swoją tożsamość. Pozwoliłoby to złośliwemu zestawowi na ominięcie weryfikacji.|  
|||  
|`-Vu  assembly`|Wyrejestrowuje *zestaw* do pominięcia weryfikacji. Te same reguły nazewnictwa zestawów, które mają zastosowanie do- **VR** , mają zastosowanie do **-VU**.|  
|`-Vx`|Usuwa wszystkie wpisy o pomijaniu weryfikacji.|  
|`-?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
> We wszystkich opcjach Sn.exe rozróżniana jest wielkość liter i opcje muszą być wpisywane dokładnie tak, jak to zostało pokazane, aby zostały rozpoznane przez narzędzie.  
  
## <a name="remarks"></a>Uwagi  
 Opcje **-R** i **– RC** są przydatne w przypadku zestawów, które zostały podpisane z opóźnieniem. W tym scenariuszu tylko klucz publiczny został ustawiony podczas kompilacji, a podpisanie wykonywane jest później, gdy znany jest klucz prywatny.  
  
> [!NOTE]
> W przypadku parametrów (na przykład-**VR)** zapisywania do chronionych zasobów, takich jak rejestr, uruchom program SN. exe jako administrator.  
  
Narzędzie silnej nazwy zakłada, że pary kluczy publiczny/prywatny są generowane przy użyciu identyfikatora algorytmu `AT_SIGNATURE`. Pary kluczy publicznych/prywatnych wygenerowane z algorytmem `AT_KEYEXCHANGE` generują błąd. 

## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy nową, losową parę kluczy i zapisuje ją w `keyPair.snk`.  
  
```console  
sn -k keyPair.snk  
```  
  
 Następujące polecenie przechowuje klucz w `keyPair.snk` w kontenerze `MyContainer` w programie CSP o silnej nazwie.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Następujące polecenie wyodrębnia klucz publiczny z `keyPair.snk` i zapisuje je w `publicKey.snk`.  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Następujące polecenie wyświetla klucz publiczny i token klucza publicznego zawarte w `publicKey.snk`.  
  
```console  
sn -tp publicKey.snk  
```  
  
 Poniższe polecenie weryfikuje `MyAsm.dll`zestawu.  
  
```console  
sn -v MyAsm.dll  
```  
  
 Następujące polecenie usuwa `MyContainer` z domyślnego dostawcy CSP.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
