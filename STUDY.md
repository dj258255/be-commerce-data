# 공부 목록

이 프로젝트를 끝까지 가면 아래 항목을 전부 한 번씩 손으로 확인하게 됩니다. 항목 옆 괄호는 그 항목을 실험하는 장과 실험 번호, 개념을 먼저 읽을 블로그 편입니다.

블로그 주소 앞부분은 `https://dj258255.github.io/IT-Oasis/blog/data/` 입니다.

## 0. SQL과 데이터 모델링

- [ ] grain: 테이블에서 행 하나가 무엇을 뜻하는가, 자연키와 대리키 (1장 E1-1)
- [ ] 조인 카디널리티와 행 증식, 중복 집계 (1장 E1-1)
- [ ] 같은 "매출"의 여러 정의: 승인 금액, 취소 반영 금액, 잔액 (1장 E1-3)
- [ ] 날짜 경계와 시간대: UTC 시각과 KST 영업일 (1장 E1-2)
- [ ] 윈도 함수와 증분 집계 (1장 E1-3, 2장 E2-2)
- [ ] 사실 테이블과 차원 테이블, 변경 이력(SCD Type 1, 2) (6장 E6-1)
- [ ] 실행 계획 읽기(`EXPLAIN ANALYZE`) (1장 E1-4)

## 1. 배치와 오케스트레이션

- [ ] 오케스트레이터가 맡는 일 (2장, 블로그 `orchestration/de-02-what-orchestrator-does`)
- [ ] 멱등성, 재시도, 백오프 (2장 E2-1, `foundations/de-03-idempotency-retry-backoff`)
- [ ] 논리 날짜와 backfill (2장 E2-3, `foundations/de-04-logical-date-backfill`)
- [ ] 스케줄 트리거와 이벤트 트리거 (2장, `orchestration/de-05-schedule-vs-event-trigger`)
- [ ] 동시성 제한 (2장 E2-3, `orchestration/de-06-concurrency-dedup-approval`)
- [ ] 파티션 덮어쓰기와 MERGE/UPSERT (2장 E2-1)
- [ ] 잠정치와 확정치, 마감 (2장 E2-2)
- [ ] 작업 성공과 데이터 정확성의 차이, 건수·신선도 검사 (2장 E2-4)

## 2. CDC

- [ ] MySQL binlog: ROW 형식, 전후 이미지, GTID (3장)
- [ ] Debezium 초기 스냅샷과 스트리밍 전환 (3장 E3-1)
- [ ] 커넥터 오프셋 저장과 재시작 뒤 중복 (3장 E3-2)
- [ ] 로그 보존이 먼저 끝나면 생기는 일과 재스냅샷 (3장 E3-3)
- [ ] DDL과 스키마 이력 토픽 (3장 E3-4)
- [ ] 비교: PostgreSQL 복제 슬롯과 `max_slot_wal_keep_size` (3장 README의 비교 절)
- [ ] CDC로 레이크하우스 채우기 (블로그 `lakehouse/de-20-cdc-to-lakehouse`)

## 3. Kafka

- [ ] 로그, 세그먼트, 오프셋, 파티션, 키 해시, 컨슈머 그룹 (4장, `streaming/de-11-kafka-log-partition-group`)
- [ ] 프로듀서의 batch, linger, acks, idempotence (4장 E4-1, `streaming/de-12-kafka-producer-latency`)
- [ ] 복제: 리더와 팔로워, ISR, high watermark, `min.insync.replicas` (4장 E4-1)
- [ ] unclean leader election (4장 E4-2)
- [ ] 오프셋 커밋 시점과 중복·유실 (4장 E4-3)
- [ ] 리밸런스: eager, cooperative-sticky, static membership, 새 컨슈머 프로토콜 (4장 E4-4)
- [ ] lag: 건수 lag과 시간 lag (4장 E4-5)
- [ ] 보존, 컴팩션, tombstone, `delete.retention.ms` (4장 E4-6)
- [ ] 파티션 수와 hot key (4장 E4-7)
- [ ] 롤링 재시작과 업그레이드 중 클라이언트가 보는 것 (4장 E4-8)
- [ ] 장애 뒤 따라잡기 용량 계산 (4장 E4-9)
- [ ] KRaft 컨트롤러 쿼럼과 메타데이터 (4장 README의 KRaft 절)
- [ ] 전달 보장, 트랜잭션, `read_committed` (5장 E5-3, `foundations/de-13-delivery-semantics`)
- [ ] 스키마 레지스트리 호환성 (7장 E7-4, `foundations/de-14-schema-registry-compatibility`)
- [ ] Kafka Connect: 워커, 태스크, 컨버터, `errors.tolerance`, DLQ (7장 E7-3)
- [ ] 운영 지표: UnderReplicatedPartitions, ISR 축소, 요청 지연, 디스크 (4장 E4-8)

## 4. 스트림 처리(Flink)

- [ ] 이벤트 시간, watermark, 늦은 데이터 (5장 E5-1, `streaming/de-15-flink-time-watermark`)
- [ ] 처리 시간 윈도가 틀리는 경우 (5장 E5-2)
- [ ] 윈도와 join (5장 E5-6, `streaming/de-16-flink-window-join`)
- [ ] 체크포인트와 장애 복구, 백프레셔 (5장 E5-3·E5-5, `streaming/de-17-flink-checkpoint-backpressure`)
- [ ] savepoint, uid, 상태가 있는 작업의 배포 (5장 E5-4)

## 5. 레이크하우스(Iceberg)

- [ ] 스냅샷과 메타데이터 구조 (6장, `lakehouse/de-18-iceberg-table-format`)
- [ ] MERGE와 삭제 파일(position, equality) (6장 E6-1)
- [ ] 작은 파일과 컴팩션 (6장 E6-2, `lakehouse/de-19-iceberg-maintenance`)
- [ ] 스냅샷 만료, orphan 파일 정리 (6장 E6-3)
- [ ] 여러 테이블의 공개 시점, write-audit-publish와 브랜치 (6장 E6-4)
- [ ] 파티션 진화 (6장 E6-5)

## 6. 운영과 정확성

- [ ] 신선도, 완전성, 정확성 지표와 SLO (7장 E7-2)
- [ ] 원본과 목적지 대조: 건수, 합계, 해시 (7장 E7-1)
- [ ] 종단 지연을 구간별로 나누기 (7장 E7-2, 측정법은 `foundations/de-08-latency-percentiles`, `foundations/de-09-measurement-pitfalls`)
- [ ] DLQ와 재처리 (7장 E7-3)
- [ ] 스키마 의미 변경 감지 (7장 E7-4)
- [ ] 백업·재생과 삭제했던 행 (7장 E7-5)
- [ ] 펜싱 (7장 E7-6)
- [ ] 장애 대응 표: 자동 재시작, 헬스체크, 지연 경보, DLQ, 무중단 배포, 버전, 백업, 분산, 로깅 (7장 E7-7)

## 7. 고난도

- [ ] 영향받은 범위만 다시 계산 (8장 E8-1)
- [ ] 실시간 결과와 재생 결과 비교 (8장 E8-2)
- [ ] 작업 대량 재시작과 제어 평면 부하 (8장 E8-3)
