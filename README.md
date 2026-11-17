# hdtSMP64 = Settle + GTSoftBody bridge + Discontinuity Guard + GPUSMP owner API, AVX2 + PDB

Base   : https://github.com/Flob26/Settle-hdtSMP64 @ ab97519 (= FSMP v4.1.1 + Settle)
Patch  : patch/settle_bridge_guard_layoutsafe.patch =
  - bridge GTSoftBody
  - FSMP-Discontinuity-Guard (YoucefNabil), state dipindah KELUAR dari SkyrimSystem/SkyrimPhysicsWorld
  - upstream PR #479 (mesh owner API) + #480 (frame events) dari DaymareOn/hdtSMP64
    -> plugin interface 2.2.0, dibutuhkan GPUSMPPhysicsNG (alandtse)
  - static_assert(sizeof(SkyrimSystem)==192) supaya Banner Physics tetap menerima build ini

PluginAPI.h / PluginOwnerAPI.h hasil build identik dengan salinan vendored di repo GPUSMPPhysicsNG.

Matikan Guard tanpa build ulang: hdtSkinnedMeshConfigs/configs.json -> "guardDiscontinuities": false
Matikan GPU: GPUSMPPhysicsNG/Settings.json -> "Enabled": false

Cara pakai: upload isi folder ke repo GitHub -> Actions -> Run workflow -> unduh artifact
`hdtSMP64-Settle-GTBridge-Guard-Owner-avx2-with-pdb` -> taruh hdtSMP64.dll + hdtSMP64.pdb BERSAMA
di satu folder mod yang menang atas Settle dan Faster HDT-SMP. Plugin GPUSMPPhysicsNG dipasang terpisah.
