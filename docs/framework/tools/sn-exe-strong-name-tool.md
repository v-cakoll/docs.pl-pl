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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a8c7ce090b286db9d86e0fc6c54ae33e7e2d5e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191890"
---
# <a name="snexe-strong-name-tool"></a>Sn.exe (Narzędzie silnych nazw)
Narzędzie silnych nazw (Sn.exe) pomaga podpisywać zestawy za pomocą [silnych nazw](../../../docs/framework/app-domains/strong-named-assemblies.md). Sn.exe dostarcza opcje do zarządzania kluczami, generowania podpisów i ich weryfikacji.  
  
> [!WARNING]
> Nie należy polegać na silne nazwy dla zabezpieczeń. Zapewniają one tylko unikatową tożsamość.

 Aby uzyskać więcej informacji na temat — silne nazwy i zestawy o silnych nazwach, zobacz [zestawy Strong-Named](../../../docs/framework/app-domains/strong-named-assemblies.md) i [jak: Podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
 Narzędzie silnych nazw jest automatycznie instalowane z Visual Studio. Aby uruchomić to narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  

> [!NOTE]
>  Na komputerach 64-bitowych należy uruchomić przy użyciu wiersza polecenia dewelopera dla programu Visual Studio i 64-bitowej wersji przy użyciu wiersza polecenia Win64 programu Visual Studio x64 32-bitowej wersji programu Sn.exe. 
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
sn [-quiet][option [parameter(s)]]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Opcja|Opis|  
|------------|-----------------|  
|**-a** *identityKeyPairFile* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> danych do migracji klucza tożsamości do klucza podpisu z pliku.|  
|**-ac** *identityPublicKeyFile* *identityKeyPairContainer* *signaturePublicKeyFile*|Generuje <xref:System.Reflection.AssemblySignatureKeyAttribute> danych do migracji klucza tożsamości do klucza podpisu z kontenera kluczy.|  
|**-c** [*csp*]|Określa domyślnego dostawcę usług kryptograficznych (CSP) do podpisywania silnymi nazwami. To ustawienie odnosi się do całego komputera. Jeśli nie określisz nazwy CSP, Sn.exe wyczyści bieżące ustawienie.|  
|**-d** *kontenera*|Usuwa określony kontener kluczy z CSP silnej nazwy.|  
|**-D**  *assembly1 assembly2*|Weryfikuje, czy dwa zestawy różnią się tylko podpisem. Jest to często używane jako sprawdzenie po ponownym podpisaniu zestawu inną parą kluczy.|  
|**-e**  *outfile zestawu*|Wyodrębnia klucz publiczny z *zestawu* i zapisuje go w *outfile.*|  
|**-h**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**-i** *infile container*|Instaluje parę kluczy z *infile* w określonym kontenerze kluczy. Kontener kluczy mieści się w CSP silnej nazwy.|  
|**-k** [*keysize*] *outfile*|Generuje nowy <xref:System.Security.Cryptography.RSACryptoServiceProvider> kluczy o określonym rozmiarze i zapisuje go do określonego pliku.  Oba klucze, publiczny i prywatny, są zapisywane do pliku.<br /><br /> Jeśli nie określono rozmiaru klucza, w przypadku gdy zainstalowany jest ulepszony dostawca kryptograficzny firmy Microsoft, domyślnie generowany jest 1024-bitowy klucz; w przeciwnym wypadku, generowany jest 512-bitowy klucz.<br /><br /> *Keysize* parametr obsługuje długości kluczy od 384 bitów do 16 384 bitów rosnąco co 8 bitów, jeśli firmy Microsoft jest ulepszony dostawca kryptograficzny zainstalowane.  Obsługuje on długości kluczy od 384 bitów do 512 bitów rosnąco co 8 bitów, jeśli zainstalowany jest podstawowy dostawca kryptograficzny firmy Microsoft.|  
|**-m** [**y** *&#124;* **n**]|Określa, czy kontenery kluczy są specyficzne dla komputera, czy dla użytkownika. Jeśli określisz *y*, kontenery kluczy są specyficzne dla komputera. Jeśli określisz *n*, kontenery kluczy są specyficzne dla użytkownika.<br /><br /> Jeśli nie podano ani y ani n, ta opcja wyświetla bieżące ustawienie.|  
|**-o**  *infile* [*outfile*]|Wyodrębnia klucz publiczny z *infile* i zapisuje je w pliku CSV. Poszczególne bajty klucza publicznego są rozdzielone przecinkami. Ten format jest użyteczny dla trwale zakodowanych odwołań do kluczy, takich jak zainicjowane tablice w kodzie źródłowym. Jeśli nie określisz *outfile*, ta opcja umieszcza wartość wyjściową w Schowku. **Uwaga:**  Ta opcja nie weryfikuje, czy na wejściu podano tylko klucz publiczny. Jeśli `infile` zawiera parę kluczy z kluczem prywatnym, klucz prywatny jest on także wyodrębniany.|  
|**-p** *infile outfile* [*hashalg*]|Wyodrębnia klucz publiczny z pary kluczy w *infile* i zapisuje go w *outfile*, opcjonalnie używając algorytmu RSA określonego przez *hashalg*. Ten klucz publiczny może być używany do opóźnione podpisywanie zestawu przy użyciu **/delaysign+** i **/KeyFile** opcje [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md). Gdy zestaw jest podpisany z opóźnieniem, w czasie kompilacji ustawiany jest tylko klucz publiczny i rezerwowana jest przestrzeń w pliku na późniejsze dodanie podpisu, gdy znany będzie klucz prywatny.|  
|**-pc**  *kontenera* *outfile* [*hashalg*]|Wyodrębnia klucz publiczny z pary kluczy w *kontenera* i zapisuje go w *outfile*. Jeśli używasz *hashalg* opcji algorytmu RSA służy do wyodrębniania klucza publicznego.|  
|**-Pb** [**y** *&#124;* **n**]|Określa, czy wymuszona jest zasada obejścia silnej nazwy. Jeśli określisz *y*, silne nazwy dla zestawów pełnego zaufania nie są weryfikowane podczas ładowania do pełnego zaufania <xref:System.AppDomain>. Jeśli określisz *n*, silne nazwy są Walidowane pod kątem poprawności, ale nie dla określonej silnej nazwy. <xref:System.Security.Permissions.StrongNameIdentityPermission> Nie ma wpływu na zestawów pełnego zaufania. Musisz wykonać swoje własne sprawdzenie dopasowania silnej nazwy.<br /><br /> Jeśli żadna `y` ani `n` jest określona, ta opcja wyświetla bieżące ustawienie. Wartość domyślna to `y`. **Uwaga:**  Na komputerach 64-bitowych należy ustawić ten parametr w każdym wystąpieniu Sn.exe, zarówno 32-bitowym, jak i 64-bitowym.|  
|**-q**[**uiet**]|Określa tryb cichy; pomija wyświetlanie komunikatów o powodzeniu.|  
|**-R**[**a**] *zestawu* *PlikWejściowy*|Podpisuje ponownie wcześniej podpisane lub podpisane z opóźnieniem zestawy parą kluczy w *infile*.<br /><br /> Jeśli **-Ra** jest używany, skróty są obliczane ponownie dla wszystkich plików w zestawie.|  
|**Rc —**[**a**] *kontenera zestawu*|Podpisuje ponownie wcześniej podpisane lub podpisane z opóźnieniem zestawy parą kluczy w *kontenera*.<br /><br /> Jeśli **— analiza głównej przyczyny** jest używany, skróty są obliczane ponownie dla wszystkich plików w zestawie.|  
|**-Rh** *zestawu*|Oblicza ponownie skróty dla wszystkich plików w zestawie.|  
|**-t**[**p**] *infile*|Wyświetla token dla klucza publicznego zapisanego w *infile*. Zawartość *infile* musi być kluczem publicznym poprzednio wygenerowanym z pliku pary kluczy przy użyciu **-p**.  Nie używaj **-t [p]** opcji do wyodrębnienia tokenu bezpośrednio z pliku pary kluczy.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe języka wspólnego zapisuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. **- Tp** opcji wyświetla także klucz publiczny oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> zastosowano atrybut do zestawu, token jest do klucza tożsamości i wyświetlana jest nazwa algorytmu wyznaczania wartości skrótu oraz klucz tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|**-T**[**p**] *assembly*|Wyświetla token klucza publicznego dla *zestawu.* *Zestawu* musi być nazwą pliku zawierającego manifest zestawu.<br /><br /> Sn.exe oblicza token przy użyciu funkcji skrótu z klucza publicznego. Aby zaoszczędzić przestrzeń, środowisko uruchomieniowe przechowuje tokeny klucza publicznego w manifeście jako część odwołania do innego zestawu, gdy rejestruje zależność do zestawu z silną nazwą. **- Tp** opcji wyświetla także klucz publiczny oprócz tokenu. Jeśli <xref:System.Reflection.AssemblySignatureKeyAttribute> zastosowano atrybut do zestawu, token jest do klucza tożsamości i wyświetlana jest nazwa algorytmu wyznaczania wartości skrótu oraz klucz tożsamości.<br /><br /> Zauważ, że ta opcja nie weryfikuje podpisu zestawu i nie powinna być używana do podejmowania decyzji dotyczących zaufania.  Ta opcja wyświetla jedynie surowe dane tokenu klucza publicznego.|  
|`-TS` `assembly` `infile`|Podpisuje testowo podpisany lub częściowo podpisany `assembly` parą kluczy w `infile`.|  
|-`TSc` `assembly` `container`|Podpisuje testowo podpisany lub częściowo podpisany `assembly` parą kluczy w kontenerze kluczy `container`.|  
|**-v** *zestawu*|Weryfikuje silną nazwę w *zestawu*, gdzie *zestawu* jest nazwą pliku zawierającego manifest zestawu.|  
|**-vf**  *zestawu*|Weryfikuje silną nazwę w *zestawu.* W odróżnieniu od **- v** opcji **-vf** wymusza weryfikację, nawet jeśli jest wyłączone, za pomocą **- Vr** opcji.|  
|**-Vk**  *regfile.reg* *zestawu* [*userlist*] [*infile*]|Tworzy plik wpisów rejestracji (reg), którego można użyć do zarejestrowania określonego zestawu, aby pomijał weryfikację. Zasady nazewnictwa zestawów, które są stosowane do **- Vr** opcja dotyczy **— Vk** także. Aby uzyskać informacje o *userlist* i *infile* opcji, zobacz **— Vr** opcji.|  
|**-Licencjonowania zbiorowego**|Wyświetla listę bieżących ustawień dla weryfikacji silnych nazw na tym komputerze.|  
|**-Vr**  *zestawu* [*userlist*] [*infile*]|Rejestruje *zestawu* do pomijania weryfikacji. Opcjonalnie można określić listę rozdzielonych przecinkami nazw użytkownika, do których powinno zostać zastosowane pominięcie weryfikacji. Jeśli określisz *infile*, weryfikacja pozostanie włączona, ale klucz publiczny w *infile* jest używany podczas operacji weryfikacji. Można określić *zestawu* w formie  *\*, strongname* Aby zarejestrować wszystkie zestawy z określoną silną nazwą. Aby uzyskać *strongname*, określ ciąg cyfr szesnastkowych reprezentujący tokenami formularza klucza publicznego. Zobacz **-t** i **-T** opcje, aby wyświetlić token klucza publicznego. **Uwaga:**  Używaj tej opcji tylko podczas tworzenia oprogramowania. Dodanie zestawu, który będzie pomijał listę weryfikacji, tworzy lukę w zabezpieczeniach. Złośliwy zestaw mógłby użyć w pełni określonej nazwy (nazwy zestawu, wersji, kultury i tokenu klucza publicznego) zestawu dodanego do listy pomijania weryfikacji, aby ukryć swoją tożsamość. Pozwoliłoby to złośliwemu zestawowi na ominięcie weryfikacji.|  
|||  
|**-Vu**  *zestawu*|Wyrejestrowuje *zestawu* do pomijania weryfikacji. Te same zasady nazewnictwa zestawów, które dotyczą **- Vr** dotyczą **- Vu**.|  
|**-Vx**|Usuwa wszystkie wpisy o pomijaniu weryfikacji.|  
|**-?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  We wszystkich opcjach Sn.exe rozróżniana jest wielkość liter i opcje muszą być wpisywane dokładnie tak, jak to zostało pokazane, aby zostały rozpoznane przez narzędzie.  
  
## <a name="remarks"></a>Uwagi  
 **-R** i **— Rc** opcje są użyteczne dla zestawów, które zostały podpisane z opóźnieniem. W tym scenariuszu tylko klucz publiczny został ustawiony podczas kompilacji, a podpisanie wykonywane jest później, gdy znany jest klucz prywatny.  
  
> [!NOTE]
>  Dla parametrów (na przykład —**Vr)** , które zapisują do chronionych zasobów, takich jak rejestr Uruchom SN.exe jako administrator.  
  
Narzędzie silnych nazw przyjęto założenie, że pary kluczy publiczny/prywatny są generowane przy użyciu `AT_SIGNATURE` identyfikator algorytmu. Pary kluczy publiczny/prywatny, wygenerowane za pomocą `AT_KEYEXCHANGE` algorytm wygenerowanie błędu. 

## <a name="examples"></a>Przykłady  
 Poniższe polecenie tworzy nowy, losowy pary kluczy i zapisuje go w `keyPair.snk`.  
  
```  
sn -k keyPair.snk  
```  
  
 Poniższe polecenie zapisuje klucz w `keyPair.snk` w kontenerze `MyContainer` w silnej nazwy dostawcy usług Kryptograficznych.  
  
```  
sn -i keyPair.snk MyContainer  
```  
  
 Poniższe polecenie wyodrębnia klucz publiczny z `keyPair.snk` i zapisuje go w `publicKey.snk`.  
  
```  
sn -p keyPair.snk publicKey.snk  
```  
  
 Następujące polecenie wyświetla klucz publiczny i jego token klucza publicznego zapisanego w `publicKey.snk`.  
  
```  
sn -tp publicKey.snk  
```  
  
 Poniższe polecenie weryfikuje zestaw `MyAsm.dll`.  
  
```  
sn -v MyAsm.dll  
```  
  
 Poniższe polecenie usuwa `MyContainer` z domyślnego CSP.  
  
```  
sn -d MyContainer  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
