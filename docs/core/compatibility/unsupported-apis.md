---
title: Nieobsługiwane interfejsy API w programie .NET Core
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936972"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a>Interfejsy API, które zawsze generują wyjątki w programie .NET Core

Następujące interfejsy API zawsze będą zgłaszać <xref:System.PlatformNotSupportedException> na platformie .NET Core na wszystkich lub podzestawach platform.

Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.

> [!NOTE]
>
> - Ten artykuł jest pracą w toku. Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.
> - Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core. Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).

## <a name="system"></a>System

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | Wszystkie |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | Wszystkie |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | Wszystkie |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemcodedomcompiler"></a>System. CodeDom. Compiler

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | Wszystkie |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemconfiguration"></a>System. Configuration

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (wszystkie elementy członkowskie) | Wszystkie |

## <a name="systemconsole"></a>System. Console

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (tylko pobieranie) | Linux i macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (tylko pobieranie) | Linux i macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |

## <a name="systemdatacommon"></a>System. Data. Common

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (zgłasza <xref:System.NotSupportedException>) | Wszystkie |

## <a name="systemdiagnosticsprocess"></a>System. Diagnostics. Process

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (tylko ustaw) | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (tylko ustaw) | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko pobieranie) | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |

## <a name="systemio"></a>System.IO

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemiopipes"></a>System. IO. Pipes

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (tylko ustaw) | Linux i macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemmedia"></a>System. Media

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnet"></a>System.Net

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (platforma UWP) |

## <a name="systemnetsockets"></a>System.Net.Sockets

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemnetwebsockets"></a>System .NET. WebSockets

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | Wszystkie |

## <a name="systemreflection"></a>System. odbicie

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | Wszystkie |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | Wszystkie |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux i macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecurity"></a>System. Security

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecurityclaims"></a>System. Security. Claims

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux i macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptographypkcs"></a>System. Security. Cryptography. PKCS

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritycryptographyx509certificates"></a>System. Security. Cryptography. x509

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (tylko ustaw) | Wszystkie |

## <a name="systemsecurityauthenticationextendedprotection"></a>System. Security. Authentication. Kiedy

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemsecuritypolicy"></a>System. Security. Policy

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemserviceprocessservicecontroller"></a>System. ServiceProcess. ServiceController

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | Wszystkie |

## <a name="systemthreading"></a>System.Threading

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | Wszystkie |

## <a name="systemxml"></a>System.Xml

| Element członkowski | Platformy, które generują |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | Wszystkie |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | Wszystkie |

## <a name="see-also"></a>Zobacz także

- [Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core](../compatibility/fx-core.md)
- [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core)
- [Analizator przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md)
