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
ms.openlocfilehash: b5eee15a08dcae42263e06939c197ec0848816a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180303"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Narzędzie silnych nazw)
Narzędzie Silna nazwa (Sn.exe) pomaga w podpisywaniu zestawów z [silnymi nazwami](../../standard/assembly/strong-named.md). Sn.exe dostarcza opcje do zarządzania kluczami, generowania podpisów i ich weryfikacji.  
  
> [!WARNING]
> Nie należy polegać na silnych nazw dla bezpieczeństwa. Zapewniają one tylko unikalną tożsamość.

 Aby uzyskać więcej informacji na temat silnych nazewnictwa i zestawów o silnych nazwach, zobacz [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md) i [jak: Podpisz zestaw o silnej nazwie](../../standard/assembly/sign-strong-name.md).  
  
 Narzędzie silnych nazw jest automatycznie instalowane z Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  

> [!NOTE]
> Na komputerach 64-bitowych uruchom 32-bitową wersję programu Sn.exe przy użyciu wiersza polecenia dewelopera dla programu Visual Studio i wersji 64-bitowej przy użyciu wiersza polecenia programu Visual Studio x64 Win64.
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|`-a identityKeyPairFile signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dane w celu migracji klucza tożsamości do klucza podpisu z pliku.|  
|`-ac identityPublicKeyFile identityKeyPairContainer signaturePublicKeyFile`|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> dane w celu migracji klucza tożsamości do klucza podpisu z kontenera klucza.|  
|`-c [csp]`|Określa domyślnego dostawcę usług kryptograficznych (CSP) do podpisywania silnymi nazwami. To ustawienie odnosi się do całego komputera. Jeśli nie określisz nazwy CSP, Sn.exe wyczyści bieżące ustawienie.|  
|`-d container`|Usuwa określony kontener kluczy z CSP silnej nazwy.|  
|`-D assembly1 assembly2`|Weryfikuje, czy dwa zestawy różnią się tylko podpisem. Jest to często używane jako sprawdzenie po ponownym podpisaniu zestawu inną parą kluczy.|  
|`-e assembly outfile`|Wyodrębnia klucz publiczny z *zestawu* i przechowuje go w *pliku outfile.*|  
|`-h`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`-i infile container`|Instaluje parę kluczy z *infile w* określonym kontenerze kluczy. Kontener kluczy mieści się w CSP silnej nazwy.|  
|`-k [keysize] outfile`|Generuje nowy <xref:System.Security.Cryptography.RSACryptoServiceProvider> klucz o określonym rozmiarze i zapisuje go w określonym pliku.  Oba klucze, publiczny i prywatny, są zapisywane do pliku.<br /><br /> Jeśli nie określono rozmiaru klucza, w przypadku gdy zainstalowany jest ulepszony dostawca kryptograficzny firmy Microsoft, domyślnie generowany jest 1024-bitowy klucz; w przeciwnym wypadku, generowany jest 512-bitowy klucz.<br /><br /> Parametr *keysize* obsługuje długości kluczy od 384 bitów do 16 384 bitów w przyrostach 8 bitów, jeśli masz zainstalowanego ulepszonego dostawcę kryptograficznego firmy Microsoft.  Obsługuje on długości kluczy od 384 bitów do 512 bitów rosnąco co 8 bitów, jeśli zainstalowany jest podstawowy dostawca kryptograficzny firmy Microsoft.|  
|`-m [y|n]`|Określa, czy kontenery kluczy są specyficzne dla komputera, czy dla użytkownika. Jeśli określisz *y, kontenery*kluczy są specyficzne dla komputera. Jeśli określisz *n*, kontenery kluczy są specyficzne dla użytkownika.<br /><br /> Jeśli nie podano ani y ani n, ta opcja wyświetla bieżące ustawienie.|  
|`-o infile [outfile]`|Wyodrębnia klucz publiczny z *pliku infile* i przechowuje go w pliku csv. Poszczególne bajty klucza publicznego są rozdzielone przecinkami. Ten format jest użyteczny dla trwale zakodowanych odwołań do kluczy, takich jak zainicjowane tablice w kodzie źródłowym. Jeśli plik wyjściowy nie zostanie określony, ta opcja umieszcza dane *wyjściowe*w Schowku. **Uwaga:**  Ta opcja nie sprawdza, czy dane wejściowe są tylko kluczem publicznym. Jeśli `infile` zawiera parę kluczy z kluczem prywatnym, klucz prywatny jest również wyodrębniany.|  
|`-p infile outfile [hashalg]`|Wyodrębnia klucz publiczny z pary kluczy *w infile* i przechowuje go w *pliku outfile,* opcjonalnie przy użyciu algorytmu RSA określonego przez *hashalg*. Ten klucz publiczny może służyć do opóźniania podpisywania zestawu przy użyciu opcji **/delaysign+** i **/keyfile** [konsolidatora zestawu (Al.exe).](al-exe-assembly-linker.md) Gdy zestaw jest podpisany z opóźnieniem, w czasie kompilacji ustawiany jest tylko klucz publiczny i rezerwowana jest przestrzeń w pliku na późniejsze dodanie podpisu, gdy znany będzie klucz prywatny.|  
|`-pc container outfile [hashalg]`|Wyodrębnia klucz publiczny z pary kluczy w *kontenerze* i przechowuje go w *pliku outfile*. Jeśli używasz opcji *hashalg,* algorytm RSA jest używany do wyodrębniania klucza publicznego.|  
|`-Pb [y|n]`|Określa, czy wymuszona jest zasada obejścia silnej nazwy. Jeśli określisz *y,* silne nazwy dla zestawów pełnego zaufania nie są <xref:System.AppDomain>sprawdzane po załadowaniu do pełnego zaufania . Jeśli określisz *n*, silne nazwy są sprawdzane pod kątem poprawności, ale nie dla określonej silnej nazwy. Nie <xref:System.Security.Permissions.StrongNameIdentityPermission> ma wpływu na zestawy pełnego zaufania. Musisz wykonać swoje własne sprawdzenie dopasowania silnej nazwy.<br /><br /> Jeśli nie `y` `n` określono ani nie jest określony, ta opcja wyświetla bieżące ustawienie. Wartość domyślna to `y`. **Uwaga:**  Na komputerach 64-bitowych należy ustawić ten parametr zarówno w wystąpieniach 32-bitowych, jak i 64-bitowych sn.exe.|  
|`-q[uiet]`|Określa tryb cichy; pomija wyświetlanie komunikatów o powodzeniu.|  
|`-R[a] assembly infile`|Ponownie podpisuje wcześniej podpisany lub podpisany z opóźnieniem zestaw z parą kluczy *w infile*.<br /><br /> Jeśli używana jest **-Ra,** skróty są ponownie kompanowane dla wszystkich plików w zestawie.|  
|`-Rc[a] assembly container`|Ponownie podpisuje wcześniej podpisany lub podpisany z opóźnieniem zestaw z parą kluczy w *kontenerze*.<br /><br /> Jeśli używana jest **-Rca,** skróty są ponownie kompanowane dla wszystkich plików w zestawie.|  
|`-Rh assembly`|Oblicza ponownie skróty dla wszystkich plików w zestawie.|  
|`-t[p] infile`|Wyświetla token klucza publicznego przechowywanego *w pliku infile*. Zawartość *pliku infile* musi być kluczem publicznym wygenerowanym wcześniej z pliku pary kluczy przy użyciu **-p**.  Nie należy używać opcji **-t[p]** do wyodrębniania tokenu bezpośrednio z pliku pary kluczy.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe języka wspólnego zapisuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. Opcja **-tp** wyświetla klucz publiczny oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut został zastosowany do zestawu, token jest dla klucza tożsamości i nazwa algorytmu mieszania i klucz tożsamości jest wyświetlany.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-T[p] assembly`|Wyświetla token klucza publicznego dla *zestawu.* Zestaw *assembly* musi być nazwą pliku zawierającego manifest zestawu.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe przechowuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. Opcja **-Tp** wyświetla klucz publiczny oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> atrybut został zastosowany do zestawu, token jest dla klucza tożsamości i nazwa algorytmu mieszania i klucz tożsamości jest wyświetlany.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-TS assembly infile`|Test-podpisuje podpisany lub częściowo podpisany *zestaw* z parą kluczy *w infile*.|  
|`-TSc assembly container`|Test-podpisuje podpisany lub częściowo podpisany *zestaw* z parą kluczy w *kontenerze*kontenera kluczy .|
|`-v assembly`|Weryfikuje silną nazwę w *zestawie,* gdzie *zestaw* jest nazwą pliku, który zawiera manifest zestawu.|  
|`-vf assembly`|Weryfikuje silną nazwę w *zestawie.* W przeciwieństwie do opcji **-v,** **-vf** wymusza weryfikację, nawet jeśli jest wyłączona za pomocą opcji **-Vr.**|  
|`-Vk regfile.reg assembly [userlist] [infile]`|Tworzy plik wpisów rejestracji (reg), którego można użyć do zarejestrowania określonego zestawu, aby pomijał weryfikację. Reguły nazewnictwa zestawu, które mają zastosowanie do opcji **-Vr,** dotyczą również **–Vk.** Aby uzyskać informacje o *opcjach listy użytkowników* i *infile,* zobacz opcję **–Vr.**|  
|`-Vl`|Wyświetla listę bieżących ustawień dla weryfikacji silnych nazw na tym komputerze.|  
|`-Vr  assembly [userlist] [infile]`|Rejestruje *zestaw* do weryfikacji pomijania. Opcjonalnie można określić listę rozdzielonych przecinkami nazw użytkownika, do których powinno zostać zastosowane pominięcie weryfikacji. Jeśli określisz *infile*, weryfikacja pozostaje włączona, ale klucz publiczny *w infile* jest używany w operacjach weryfikacji. Można określić *zestaw* w formularzu * \*, strongname* zarejestrować wszystkie zestawy o określonej silnej nazwie. Dla *strongname*, określ ciąg cyfr szesnastkowych reprezentujących tokenizowaneformo klucza publicznego. Zobacz opcje **-t** i **-T,** aby wyświetlić token klucza publicznego. **Uwaga:**  Tej opcji należy używać tylko podczas tworzenia. Dodanie zestawu, który będzie pomijał listę weryfikacji, tworzy lukę w zabezpieczeniach. Złośliwy zestaw mógłby użyć w pełni określonej nazwy (nazwy zestawu, wersji, kultury i tokenu klucza publicznego) zestawu dodanego do listy pomijania weryfikacji, aby ukryć swoją tożsamość. Pozwoliłoby to złośliwemu zestawowi na ominięcie weryfikacji.|  
|||  
|`-Vu  assembly`|Wyrejestruje *zestaw* do weryfikacji pomijania. Te same zasady nazewnictwa zestawu, które mają zastosowanie do **-Vr** stosuje się do **-Vu**.|  
|`-Vx`|Usuwa wszystkie wpisy o pomijaniu weryfikacji.|  
|`-?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
> We wszystkich opcjach Sn.exe rozróżniana jest wielkość liter i opcje muszą być wpisywane dokładnie tak, jak to zostało pokazane, aby zostały rozpoznane przez narzędzie.  
  
## <a name="remarks"></a>Uwagi  
 **-R** i **-Rc** opcje są przydatne w przypadku zestawów, które zostały podpisane z opóźnieniem. W tym scenariuszu tylko klucz publiczny został ustawiony podczas kompilacji, a podpisanie wykonywane jest później, gdy znany jest klucz prywatny.  
  
> [!NOTE]
> Dla parametrów (na przykład —**Vr),** które zapisują do chronionych zasobów, takich jak rejestr, uruchom SN.exe jako administrator.  
  
Silne nazwa narzędzie zakłada, że pary kluczy publicznych/prywatnych są generowane za pomocą identyfikatora algorytmu. `AT_SIGNATURE` Pary kluczy publicznych/prywatnych `AT_KEYEXCHANGE` wygenerowane za pomocą algorytmu generują błąd.

## <a name="examples"></a>Przykłady  
 Następujące polecenie tworzy nową, losową parę `keyPair.snk`klawiszy i przechowuje ją w pliku .  
  
```console  
sn -k keyPair.snk  
```  
  
 Następujące polecenie przechowuje `keyPair.snk` klucz w `MyContainer` kontenerze w silnej nazwie CSP.  
  
```console  
sn -i keyPair.snk MyContainer  
```  
  
 Poniższe polecenie wyodrębnia klucz `keyPair.snk` publiczny i `publicKey.snk`przechowuje go w pliku .  
  
```console  
sn -p keyPair.snk publicKey.snk  
```  
  
 Następujące polecenie wyświetla klucz publiczny i token klucza `publicKey.snk`publicznego zawartego w programie .  
  
```console  
sn -tp publicKey.snk  
```  
  
 Następujące polecenie weryfikuje zestaw `MyAsm.dll`.  
  
```console  
sn -v MyAsm.dll  
```  
  
 Następujące polecenie usuwa `MyContainer` z domyślnego CSP.  
  
```console  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
