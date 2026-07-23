# leetcode

从0开始刷题记录
  场景 A:libspdm(requester)验 wolfSPDM(responder）的签名
  1. responder 侧拿到身份公钥（TPMT_PUBLIC 时先从尾部取 X‖Y，规则见 spdm_crypto.c:238-241);
  2. XyToSpkiDer() 转成 120 字节 DER;
  3. libspdm 侧：libspdm_set_data(ctx, LIBSPDM_DATA_PEER_PUBLIC_KEY, &parameter, der, 120)，并按 raw-key 模式配置（关 CERT_CAP，开 PUB_KEY_ID_CAP);
  4. KEY_EXCHANGE_RSP 里的签名两边都是 raw r‖s，无需处理。
